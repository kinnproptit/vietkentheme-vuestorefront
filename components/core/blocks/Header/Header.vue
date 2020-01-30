<template>
  <div class="header">
    <header
      class="fixed w-100 brdr-bottom-1 bg-cl-primary brdr-cl-secondary"
      :class="{ 'is-visible': navVisible }"
    >
      <div class="banner2 container">
        <div class="row">
          <div class="col-md-4 center-md">
            <a href="/kontakt">
              <svg class="advice-icon" viewBox="0 0 520 520" style="width: 14px; height: 14px">
                <path
                  d="m256 0c-141 0-256 115-256 256 0 47 12 92 36 131l-17 46-16 43 45-6 57-7c44 32 97 49 151 49 141 0 256-115 256-256 0-141-115-256-256-256z m0 484c-54 0-104-19-143-50l-68 8 22-58c-25-37-39-81-39-128 0-126 102-228 228-228 126 0 228 102 228 228 0 126-102 228-228 228z m-27-186c0-15 1-27 4-36 3-9 9-17 17-26 8-9 13-16 16-22 3-6 4-11 4-17 0-18-6-27-18-27-5 0-9 2-13 7-3 5-5 12-5 20l-47 0c0-21 6-37 18-49 11-11 27-17 47-17 21 0 37 5 48 17 12 11 17 27 17 47 0 17-7 33-21 49l-13 15c-5 6-8 11-10 17-2 6-3 13-3 22z m-5 50c0-7 3-13 8-18 4-5 11-7 18-7 8 0 14 3 19 7 4 5 7 11 7 18 0 7-3 13-7 18-5 5-11 7-19 7-8 0-14-2-19-7-4-5-7-11-7-18z"
                />
              </svg>
              Service &amp; Beratung
            </a>
          </div>
          <div class="col-md-4">Versandkostenfrei ab 100 €</div>

          <div class="col-md-4">
            <div class="website-switcher-wrapper">
              <a
                class="header-country-language store-switch-icon js-store-switch-icon"
                href="#storeswitcher"
                data-toggle-single
              >
                <span class="sprite-ico-store-de"></span>
                Land | Sprache
              </a>
            </div>
          </div>
        </div>
      </div>
      <!--  -->
      <div class="px15 brown-background">
        <div class="container">
          <div class="row between-xs middle-xs" v-if="!isCheckoutPage || isThankYouPage">
            <div class="col-md-3 col-xs-2 middle-xs hidden-md">
              <div>
                <!-- <hamburger-icon class="p15 icon bg-cl-secondary pointer" /> -->
                <logo width="auto" height="41px" />
              </div>
            </div>
            <div class="col-md-3 col-xs-2 middle-xs visible-md">
              <div>
                <hamburger-icon class="p15 icon bg-cl-secondary pointer" />
              </div>
            </div>
            <div class="col-xs-2 visible-xs">
              <search-icon class="p15 icon pointer white-color" />
            </div>
            <div class="col-md-6 col-xs-2 center-xs pt5" style="padding: 0;">
              <div class="visible-xs visible-md">
                <logo width="auto" height="41px" />
              </div>
              <div class="hidden-md">
                <custom-navbar />
              </div>
            </div>
            <div class="col-xs-2 visible-xs">
              <wishlist-icon class="p15 icon pointer white-color" />
            </div>
            <div class="col-md-3 col-xs-2 end-xs">
              <div class="inline-flex right-icons">
                <search-icon class="p15 icon hidden-xs pointer white-color" />
                <wishlist-icon class="p15 icon hidden-xs pointer white-color" />
                <!-- <compare-icon class="p15 icon hidden-xs pointer" /> -->
                <microcart-icon class="p15 icon pointer white-color" />
                <account-icon class="p15 icon hidden-xs pointer white-color" />
              </div>
            </div>
          </div>
          <div class="row between-xs middle-xs px15 py5" v-if="isCheckoutPage && !isThankYouPage">
            <div class="col-xs-5 col-md-3 middle-xs">
              <div>
                <router-link
                  :to="localizedRoute('/')"
                  class="cl-tertiary links"
                >{{ $t('Return to shopping') }}</router-link>
              </div>
            </div>
            <div class="col-xs-2 col-md-6 center-xs">
              <logo width="auto" height="41px" />
            </div>
            <div class="col-xs-5 col-md-3 end-xs">
              <div>
                <a
                  v-if="!currentUser"
                  href="#"
                  @click.prevent="gotoAccount"
                  class="cl-tertiary links"
                >{{ $t('Login to your account') }}</a>
                <span v-else>{{ $t('You are logged in as {firstname}', currentUser) }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="banner">
        <strong>Subscribe with NewScription™ and get up to 15% off + free shipping on replenishments.</strong>
        <a href="/newscription/">Learn more</a>
      </div>
    </header>
    <div class="header-placeholder" />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import CurrentPage from 'theme/mixins/currentPage'
import AccountIcon from 'theme/components/core/blocks/Header/AccountIcon'
// import CompareIcon from 'theme/components/core/blocks/Header/CompareIcon'
import HamburgerIcon from 'theme/components/core/blocks/Header/HamburgerIcon'
import Logo from 'theme/components/core/Logo'
import MicrocartIcon from 'theme/components/core/blocks/Header/MicrocartIcon'
import SearchIcon from 'theme/components/core/blocks/Header/SearchIcon'
import WishlistIcon from 'theme/components/core/blocks/Header/WishlistIcon'
import CustomNavbar from 'theme/components/theme/blocks/CustomNavbar/CustomNavbar'

export default {
  name: 'Header',
  components: {
    AccountIcon,
    // CompareIcon,
    HamburgerIcon,
    CustomNavbar,
    Logo,
    MicrocartIcon,
    SearchIcon,
    WishlistIcon
  },
  mixins: [CurrentPage],
  data() {
    return {
      navVisible: true,
      isScrolling: false,
      scrollTop: 0,
      lastScrollTop: 0,
      navbarHeight: 54
    }
  },
  computed: {
    ...mapState({
      isOpenLogin: state => state.ui.signUp,
      currentUser: state => state.user.current
    }),
    isThankYouPage() {
      return this.$store.state.checkout.isThankYouPage
        ? this.$store.state.checkout.isThankYouPage
        : false
    }
  },
  beforeMount() {
    window.addEventListener(
      'scroll',
      () => {
        this.isScrolling = true
      },
      { passive: true }
    )

    setInterval(() => {
      if (this.isScrolling) {
        this.hasScrolled()
        this.isScrolling = false
      }
    }, 250)
  },
  methods: {
    gotoAccount() {
      this.$bus.$emit('modal-toggle', 'modal-signup')
    },
    hasScrolled() {
      this.scrollTop = window.scrollY
      if (
        this.scrollTop > this.lastScrollTop &&
        this.scrollTop > this.navbarHeight
      ) {
        this.navVisible = false
      } else {
        this.navVisible = true
      }
      this.lastScrollTop = this.scrollTop
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~theme/css/variables/colors';
@import '~theme/css/helpers/functions/color';
$color-icon-hover: color(secondary, $colors-background);

header {
  height: 54px;
  top: -55px;
  z-index: 3;
  transition: top 0.2s ease-in-out;
  background: #795548;
  top: 0;
  &.is-visible {
    top: 0;
  }
}
.icon {
  opacity: 0.6;
  &:hover,
  &:focus {
    background-color: $color-icon-hover;
    opacity: 1;
  }
}
.right-icons {
  //for edge
  float: right;
}
.header-placeholder {
  height: 54px;
}
.links {
  text-decoration: underline;
}

.brown-background {
  background: #795548;
}

.white-color {
  color: #ffffff;
}

.banner {
  background: #27ae60;
  margin: 0 auto;
  width: 100%;
  text-align: center;
  padding: 0.1875rem 0;
  font-size: 15px;
  color: #ffffff;
}

.banner2 {
  background-color: #c6aa9f;
  margin: 0 auto;
  width: 100%;
  text-align: center;
  padding: 0.1875rem 0;
  font-size: 15px;
  color: #ffffff;
}

@media (max-width: 767px) {
  .row.middle-xs {
    margin: 0 -15px;

    &.py5 {
      margin: 0;
    }
  }
  .col-xs-2:first-of-type {
    padding-left: 0;
  }
  .col-xs-2:last-of-type {
    padding-right: 0;
  }
  a,
  span {
    font-size: 12px;
  }
}

@media (min-width: 1200px) {
  .hidden-md {
    display: block;
  }

  .visible-md {
    display: none;
  }
}

@media (max-width: 1199px) {
  .hidden-md {
    display: none;
  }

  .visible-md {
    display: block;
  }
}
</style>
