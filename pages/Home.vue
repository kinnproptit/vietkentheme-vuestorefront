<template>
  <div id="home">
    <head-image />

    <section class="container px15">
      <company-information />
    </section>
    <!-- <promoted-offers /> -->
    <section
      class="container px15"
      style="display: flex; flex-direction: column; justify-content: center; align-items: center;"
    >
      <div>
        <header class="col-md-12">
          <h2 class="align-center cl-accent">{{ $t('Support for your health needs.') }}</h2>
          <p
            class="align-center cl-accent"
          >We believe nature knows what's best, and that's why our passion is in helping you meet your goals and stay well the natural way.</p>
        </header>
      </div>
      <health-slider />
    </section>

    <section class="new-collection container px15" style="padding-top: 50px;">
      <div>
        <header class="col-md-12">
          <h2 class="align-center cl-accent">{{ $t('Most popular product') }}</h2>
        </header>
      </div>
      <div class="row center-xs">
        <lazy-hydrate :trigger-hydration="!loading" v-if="isLazyHydrateEnabled">
          <product-listing columns="4" :products="getEverythingNewCollection" />
        </lazy-hydrate>
        <product-listing v-else columns="4" :products="getEverythingNewCollection" />
      </div>
    </section>

    <!-- <section v-if="isOnline" class="container pb60 px15">
      <div class="row center-xs">
        <header
          class="col-md-12"
          :class="{ pt40: getEverythingNewCollection && getEverythingNewCollection.length }"
        >
          <h2 class="align-center cl-accent">{{ $t('Get inspired') }}</h2>
        </header>
      </div>
      <tile-links />
    </section>-->

    <!-- <section v-if="isOnline" class="container pb60 px15">
      <div class="row center-xs">
        <header
          class="col-md-12"
          :class="{ pt40: getEverythingNewCollection && getEverythingNewCollection.length }"
        >
          <h2 class="align-center cl-accent">Short script</h2>
        </header>
      </div>
      <short-script />
    </section>-->
    <Onboard />
  </div>
</template>

<script>
// query constructor
import { isServer, onlineHelper } from '@vue-storefront/core/helpers';
import LazyHydrate from 'vue-lazy-hydration';

// Core pages
import Home from '@vue-storefront/core/pages/Home';
// Theme core components
import ProductListing from 'theme/components/core/ProductListing';
import HeadImage from 'theme/components/core/blocks/MainSlider/HeadImage';
// Theme local components
import Onboard from 'theme/components/theme/blocks/Home/Onboard';
// import PromotedOffers from 'theme/components/theme/blocks/PromotedOffers/PromotedOffers'
import CompanyInformation from 'theme/components/theme/blocks/CompanyInformation/CompanyInformation';
import HealthSlider from 'theme/components/theme/blocks/HealthSlider/HealthSlider';
import TileLinks from 'theme/components/theme/blocks/TileLinks/TileLinks';
import ShortScript from 'theme/components/theme/blocks/ShortScript/ShortScript';
import { Logger } from '@vue-storefront/core/lib/logger';
import { mapGetters } from 'vuex';
import config from 'config';
import { registerModule } from '@vue-storefront/core/lib/modules';
import { RecentlyViewedModule } from '@vue-storefront/core/modules/recently-viewed';

export default {
  data() {
    return {
      loading: true
    };
  },
  mixins: [Home],
  components: {
    HeadImage,
    Onboard,
    ProductListing,
    // PromotedOffers,
    CompanyInformation,
    HealthSlider,
    // TileLinks,
    ShortScript,
    LazyHydrate
  },
  computed: {
    ...mapGetters('user', ['isLoggedIn']),
    ...mapGetters('homepage', ['getEverythingNewCollection']),
    categories() {
      return this.getCategories;
    },
    isOnline() {
      return onlineHelper.isOnline;
    },
    isLazyHydrateEnabled() {
      return config.ssr.lazyHydrateFor.some(field =>
        ['homepage', 'homepage.new_collection'].includes(field)
      );
    }
  },
  beforeCreate() {
    registerModule(RecentlyViewedModule);
  },
  async beforeMount() {
    if (this.$store.state.__DEMO_MODE__) {
      const onboardingClaim = await this.$store.dispatch('claims/check', {
        claimCode: 'onboardingAccepted'
      });
      if (!onboardingClaim) {
        // show onboarding info
        this.$bus.$emit('modal-toggle', 'modal-onboard');
        this.$store.dispatch('claims/set', {
          claimCode: 'onboardingAccepted',
          value: true
        });
      }
    }
  },
  mounted() {
    if (!this.isLoggedIn && localStorage.getItem('redirect')) {
      this.$bus.$emit('modal-show', 'modal-signup');
    }
  },
  watch: {
    isLoggedIn() {
      const redirectObj = localStorage.getItem('redirect');
      if (redirectObj) this.$router.push(redirectObj);
      localStorage.removeItem('redirect');
    }
  },
  async asyncData({ store, route }) {
    // this is for SSR purposes to prefetch data
    Logger.info('Calling asyncData in Home (theme)')();

    await Promise.all([
      store.dispatch('homepage/fetchNewCollection'),
      store.dispatch('promoted/updateHeadImage'),
      store.dispatch('promoted/updatePromotedOffers')
    ]);
  },
  beforeRouteEnter(to, from, next) {
    if (!isServer && !from.name) {
      // Loading products to cache on SSR render
      next(vm =>
        vm.$store.dispatch('homepage/fetchNewCollection').then(res => {
          vm.loading = false;
        })
      );
    } else {
      next();
    }
  }
};
</script>

<style lang="scss" scoped>
.new-collection {
  @media (max-width: 767px) {
    padding-top: 0;
  }
}
</style>
