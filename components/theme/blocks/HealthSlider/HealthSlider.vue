<template>
  <div class="row center-xs">
    <carousel :data="data"></carousel>
  </div>
</template>

<script>
import Vue from 'vue'
import VueCarousel from '@chenfengyuan/vue-carousel'
Vue.use(VueCarousel)
export default {
  name: 'HealthSlider',
  data() {
    return {
      data: [
        {
          id: 1,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-prenatal-postnatal.png',
          title: 'Prenatal & Postnatal',
          message:
            ' From preconception to birth to nursing, New Chapter products are there for you, every step of the way.',
          buttonUrl: '/regimens/prenatal-postnatal',
          content(createElement, content) {
            // return createElement(
            //   'div',
            //   {
            //     class:
            //       'slide sliders-item slick-slide slick-current slick-center',
            //     props: {
            //       width: 329
            //     }
            //   },
            //   [
            //     createElement(
            //       'div',
            //       {
            //         class: 'slider-image'
            //       },
            //       createElement('img', {
            //         class: 'health-goal_img',
            //         attrs: {
            //           src: `${content.imgUrl}`
            //         }
            //       })
            //     ),
            //     createElement(
            //       'div',
            //       {
            //         class: 'card-section'
            //       },
            //       [
            //         createElement('h3', `${content.title}`),
            //         createElement('p', `${content.message}`, {
            //           class: 'secondary'
            //         }),
            //         createElement('a', {
            //           class: 'button health-goal__section-button',
            //           attrs: {
            //             href: `${content.buttonUrl}`
            //           }
            //         })
            //       ]
            //     )
            //   ]
            // )
            return createElement('span', `${content.message}`)
          }
        }
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-stress.png',
        //   title: 'Stress',
        //   message:
        //     'Our vitamins and herbal supplements can help you alleviate occasional stress.*',
        //   buttonUrl: '/stress',
        //   content(createElement, content) {
        //     return createElement(
        //       'div',
        //       {
        //         class:
        //           'slide sliders-item slick-slide slick-current slick-center',
        //         props: {
        //           width: 329
        //         }
        //       },
        //       [
        //         createElement(
        //           'div',
        //           {
        //             class: 'slider-image'
        //           },
        //           createElement('img', {
        //             class: 'health-goal_img',
        //             attrs: {
        //               src: `${content.imgUrl}`
        //             }
        //           })
        //         ),
        //         createElement(
        //           'div',
        //           {
        //             class: 'card-section'
        //           },
        //           [
        //             createElement('h3', `${content.title}`),
        //             createElement('p', `${content.message}`, {
        //               class: 'secondary'
        //             }),
        //             createElement('a', {
        //               class: 'button health-goal__section-button',
        //               attrs: {
        //                 href: `${content.buttonUrl}`
        //               }
        //             })
        //           ]
        //         )
        //       ]
        //     )
        //   }
        // }
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-energy.png',
        //   title: 'Energy',
        //   message:
        //     'Maintain a balanced energy level with our vitamins and herbal supplements.*',
        //   buttonUrl: '/energy'
        // },
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/heart-health.png',
        //   title: 'Heart Health',
        //   message:
        //     'Support your heart with our 100% Wild Alaskan Salmon fish oil, vitamins, herbals, and more.*',
        //   buttonUrl: '/regimens/heart-health'
        // },
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-mens-wellness.png',
        //   title: "Men's Wellness",
        //   message:
        //     'Support heart, joint, and prostate health at every stage of a man’s life.*',
        //   buttonUrl: '/regimens/mens-wellness'
        // },
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-womens-wellness.png',
        //   title: "Women's Wellness",
        //   message:
        //     'Maintain a balanced energy level with our vitamins and herbal supplements.*',
        //   buttonUrl: '/regimens/womens-wellness'
        // },
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-inflamation.png',
        //   title: 'Inflammation',
        //   message:
        //     'Discover our herbal remedies to support pain relief† and a healthy inflammation response.*',
        //   buttonUrl: '/inflammation'
        // },
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-joint-mobility.png',
        //   title: 'Joint & Mobility',
        //   message:
        //     'See how you can strengthen your bones and maintain healthy movement and joint flexibility.*',
        //   buttonUrl: '/regimens/joint-and-mobility/'
        // },
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-immune-support.png',
        //   title: 'Immune Support',
        //   message:
        //     'Keep your immune system functioning at a normal level with our products.*',
        //   buttonUrl: '/immune-support'
        // },
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-sleep.jpg',
        //   title: 'Sleep',
        //   message:
        //     'Support a restful night’s sleep with whole-food, targeted herbs.*',
        //   buttonUrl: '/sleep'
        // },
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-beauty.jpg',
        //   title: 'Beauty',
        //   message:
        //     'Promotes a youthful appearance with clinically proven results.*',
        //   buttonUrl: '/beauty'
        // },
        // {
        //   imgUrl:
        //     'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-healthy-aging.jpg',
        //   title: 'Healthy Aging',
        //   message:
        //     'Feel empowered year after year with supplements for healthy aging.',
        //   buttonUrl: '/healthy-aging'
        // }
      ]
    }
  }

  // methods: {
  //   content(createElement, data, vm) {
  //     return createElement('div', {
  //       class: 'example-slide',
  //     }, [`Slide ${vm.$parent.direction}`]);
  //   },
  // },
}
</script>

<style lang="scss" scoped>
.slide {
  align-items: center;
  background-color: #666;
  color: #999;
  display: flex;
  font-size: 1.5rem;
  justify-content: center;
  min-height: 10rem;
}

.button {
  border-style: solid;
  border-width: 1px;
  cursor: pointer;
  font-weight: 400;
  margin: 0 0 1rem;
  position: relative;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  background-color: transparent;
  border-color: #ccc;
  color: #666;
  font-size: 1rem;
  padding: 0.875rem 2.25rem;
  border-radius: 4px;
  outline: 0;
  vertical-align: middle;
}

.health-goal__section-button {
  background-color: #795548;
  border-color: #795548;
  color: #fefefe;
}

.slick-slide {
  float: left;
  height: 100%;
  min-height: 1px;
}

.slick-initialized .slick-slide {
  display: block;
}

.sliders-item:before {
  top: 0;
  content: '';
  bottom: 0;
  left: 0;
  right: 0;
  width: 100%;
  position: absolute;
  background-color: rgba(255, 255, 255, 0.5);
}

.sliders-item,
.slick-current:before {
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
  background-color: transparent;
}

.slider-image img {
  max-width: 100%;
}
</style>
