/* eslint-disable vue/singleline-html-element-content-newline */
<template>
  <div class="row center-xs">
    <carousel :mouse-drag="false" :per-page="1">
      <slide v-for="item in data" :key="item.id">
        <div class="sliders-item" :key="item.id">
          <div class="slider-image">
            <img class="health-goal_img" :src="item.imgUrl" alt="Health needs" />
          </div>
          <div class="card-section">
            <h3>{{ item.title }}</h3>
            <p class="secondary">{{ item.message }}</p>
            <a class="button health-goal__section-button" :href="item.buttonUrl">LEARN MORE</a>
          </div>
        </div>
      </slide>
    </carousel>
  </div>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel'
import Vue from 'vue'
import VueCarousel from 'vue-carousel'

Vue.use(VueCarousel)
export default {
  name: 'HealthSlider',
  components: {
    Carousel,
    Slide
  },
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
          buttonUrl: '/regimens/prenatal-postnatal'
        },
        {
          id: 2,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-stress.png',
          title: 'Stress',
          message:
            'Our vitamins and herbal supplements can help you alleviate occasional stress.*',
          buttonUrl: '/stress'
        },
        {
          id: 3,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-energy.png',
          title: 'Energy',
          message:
            'Maintain a balanced energy level with our vitamins and herbal supplements.*',
          buttonUrl: '/energy'
        },
        {
          id: 4,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/heart-health.png',
          title: 'Heart Health',
          message:
            'Support your heart with our 100% Wild Alaskan Salmon fish oil, vitamins, herbals, and more.*',
          buttonUrl: '/regimens/heart-health'
        },
        {
          id: 5,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-mens-wellness.png',
          title: "Men's Wellness",
          message:
            'Support heart, joint, and prostate health at every stage of a man’s life.*',
          buttonUrl: '/regimens/mens-wellness'
        },
        {
          id: 6,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-womens-wellness.png',
          title: "Women's Wellness",
          message:
            'Maintain a balanced energy level with our vitamins and herbal supplements.*',
          buttonUrl: '/regimens/womens-wellness'
        },
        {
          id: 7,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-inflamation.png',
          title: 'Inflammation',
          message:
            'Discover our herbal remedies to support pain relief† and a healthy inflammation response.*',
          buttonUrl: '/inflammation'
        },
        {
          id: 8,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-joint-mobility.png',
          title: 'Joint & Mobility',
          message:
            'See how you can strengthen your bones and maintain healthy movement and joint flexibility.*',
          buttonUrl: '/regimens/joint-and-mobility/'
        },
        {
          id: 9,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-immune-support.png',
          title: 'Immune Support',
          message:
            'Keep your immune system functioning at a normal level with our products.*',
          buttonUrl: '/immune-support'
        },
        {
          id: 10,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-sleep.jpg',
          title: 'Sleep',
          message:
            'Support a restful night’s sleep with whole-food, targeted herbs.*',
          buttonUrl: '/sleep'
        },
        {
          id: 11,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-beauty.jpg',
          title: 'Beauty',
          message:
            'Promotes a youthful appearance with clinically proven results.*',
          buttonUrl: '/beauty'
        },
        {
          id: 12,
          imgUrl:
            'https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/health-goals/health-goal-slider-healthy-aging.jpg',
          title: 'Healthy Aging',
          message:
            'Feel empowered year after year with supplements for healthy aging.',
          buttonUrl: '/healthy-aging'
        }
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

.sliders-item {
  background-color: rgba(255, 255, 255, 0.5);
  width: 329px;
  display: inline-block;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
  height: 99%;
}

.slider-image img {
  max-width: 100%;
}

.card-section {
  padding-bottom: 48px;
  padding: 48px 30px 66px;
  transition: opacity 0.3s ease;
}
</style>
