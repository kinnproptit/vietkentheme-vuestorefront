<template>
  <ul class="navList" id="menu">
    <li class="bg-cl">
      <a
        class="block px25 py17 brdr-cl-secondary cl-accent no-underline fs-medium-small w-cl"
        href="#"
        title="Menu"
      >{{ $t('Products') }}</a>
      <div class="submenu">
        <ul class="menus">
          <li>
            <router-link
              class="bg-cl-transparent brdr-none fs-small"
              :to="localizedRoute('/all-2')"
              exact
            >{{ $t('All Products') }}</router-link>
          </li>
          <li :key="category.slug" v-for="category in visibleCategories">
            <router-link
              class="bg-cl-transparent brdr-none fs-small"
              :to="categoryLink(category)"
            >{{ category.name }}</router-link>
          </li>
        </ul>
      </div>
      <!-- <ul class="menus">
          <router-link
            class="block px25 py17 cl-accent no-underline"
            :to="localizedRoute('/all-2')"
            exact
          >{{ $t('All Products') }}</router-link>
          <li class="flex" :key="category.slug" v-for="category in visibleCategories">
            <div v-if="isCurrentMenuShowed" class="subcategory-item">
              <sub-btn
                v-if="category.children_count > 0"
                class="bg-cl-transparent brdr-none fs-medium"
                :id="category.id"
                :name="category.name"
              />
              <router-link
                v-else
                class="px25 py17 cl-accent no-underline col-xs"
                :to="categoryLink(category)"
              >{{ category.name }}</router-link>
            </div>

            <sub-category
              :category-links="category.children_data"
              :id="category.id"
              :parent-slug="category.slug"
              :parent-path="category.url_path"
            />
          </li>
      </ul>-->
    </li>
    <li v-if="isCurrentMenuShowed" class="bg-cl">
      <router-link
        class="block px25 py17 brdr-cl-secondary cl-accent no-underline fs-medium-small w-cl"
        :to="localizedRoute('/health-needs')"
        exact
      >{{ $t('Health Needs') }}</router-link>
    </li>
    <li v-if="isCurrentMenuShowed" class="bg-cl">
      <router-link
        class="block px25 py17 brdr-cl-secondary cl-accent no-underline fs-medium-small w-cl"
        :to="localizedRoute('/ingredients')"
        exact
      >{{ $t('Ingredients') }}</router-link>
    </li>
    <li v-if="isCurrentMenuShowed" class="bg-cl">
      <router-link
        class="block px25 py17 brdr-cl-secondary cl-accent no-underline fs-medium-small w-cl"
        :to="localizedRoute('/i/about-us')"
        exact
      >{{ $t('About Us') }}</router-link>
    </li>
    <li v-if="isCurrentMenuShowed" class="bg-cl">
      <router-link
        class="block px25 py17 brdr-cl-secondary cl-accent no-underline fs-medium-small w-cl"
        :to="localizedRoute('/rewards')"
        exact
      >{{ $t('Rewards') }}</router-link>
    </li>
  </ul>
</template>

<script>
import { mapState } from 'vuex'
import i18n from '@vue-storefront/i18n'
import SidebarMenu from '@vue-storefront/core/compatibility/components/blocks/SidebarMenu/SidebarMenu'
import SubBtn from 'theme/components/core/blocks/SidebarMenu/SubBtn'
import SubCategory from 'theme/components/core/blocks/SidebarMenu/SubCategory'
import { formatCategoryLink } from '@vue-storefront/core/modules/url/helpers'
import { disableBodyScroll, clearAllBodyScrollLocks } from 'body-scroll-lock'

export default {
  name: 'CustomNavbar',
  components: {
    SubCategory,
    SubBtn
  },
  mixins: [SidebarMenu],
  computed: {
    mainListStyles() {
      return this.submenu.depth
        ? `transform: translateX(${this.submenu.depth * 100}%)`
        : false
    },
    ...mapState({
      submenu: state => state.ui.submenu,
      currentUser: state => state.user.current
    }),
    getSubmenu() {
      return this.submenu
    },
    visibleCategories() {
      return this.categories.filter(category => {
        return category.product_count > 0 || category.children_count > 0
      })
    },
    isCurrentMenuShowed() {
      return true
    }
  },
  methods: {
    login() {
      if (!this.currentUser && this.isCurrentMenuShowed) {
        this.$nextTick(() => {
          this.$store.commit('ui/setAuthElem', 'login')
          this.$bus.$emit('modal-show', 'modal-signup')
          this.$router.push({ name: 'my-account' })
        })
      }
    },
    categoryLink(category) {
      return formatCategoryLink(category)
    }
  }
}
</script>

<style lang="scss" scoped>
// @import '~theme/css/animations/transitions';
// @import '~theme/css/variables/colors';
// @import '~theme/css/helpers/functions/color';
// $bg-secondary: color(secondary, $colors-background);
// $color-gainsboro: color(gainsboro);
// $color-matterhorn: color(matterhorn);
// $color-mine-shaft: color(mine-shaft);

// .sidebar-menu {
//   height: 100vh;
//   width: 350px;
//   overflow: hidden;

//   @media (max-width: 767px) {
//     width: 100vh;
//   }

//   &__container {
//     overflow-y: auto;
//     -webkit-overflow-scrolling: touch;
//     height: calc(100% - 55px);
//   }

//   &__list {
//     transition: transform $duration-main $motion-main;
//   }

//   ul {
//     list-style-type: none;
//   }

//   li {
//     &:hover,
//     &:focus {
//       background-color: $color-gainsboro;
//     }
//     &.bg-cl-primary {
//       &:hover,
//       &:focus {
//         background-color: $bg-secondary;
//       }
//     }
//     a {
//       color: $color-mine-shaft;
//     }
//   }

//   .subcategory-item {
//     display: flex;
//     width: 100%;
//   }

//   button {
//     color: $color-mine-shaft;
//     a {
//       color: $color-mine-shaft;
//     }
//   }
// }

.navList {
  padding: 0;
  margin: 0;
  display: flex;
  list-style: none;
}

.py17 {
  padding-top: 17px;
  padding-bottom: 20px;
}

.bg-cl {
  background-color: #795548;
  &:hover {
    background-color: white;
  }
}

.w-cl {
  color: white;
  &:hover {
    color: #000000;
  }
}

.submenu {
  height: auto;
  max-width: 400px;
  position: absolute;
  z-index: 99;
  display: none;
  border: 0;
  background-color: #fefefe;
  padding: 0.75rem 1.5rem !important;
  text-align: left;
}

ul.menus {
  max-width: 75.25rem;
  width: 100%;
  border-left: 0;
  margin: auto;
  padding-left: 0;
}

.menus li {
  display: block;
  width: 100%;
  font: 12px Arial;
  padding: 0.75rem;
}

#menu li:hover .submenu {
  display: block;
  &.w-cl {
    color: black;
  }
}
.fs-small {
  font-size: 14px;
}
</style>
