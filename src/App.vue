<template>
  <navigation-bar></navigation-bar>
  <div><logo-nav-bar></logo-nav-bar></div>
  <main>
    <picture-navigation></picture-navigation>
  </main>

  <div class="page-main">
    <div class="main">
      <div style="height: 22px; width: 1226px; background-color: #f5f5f5; margin-top: 16px"></div>
      <div class="home-banner-box">
        <img src="../public/xiaomi/homeBanner.webp" alt="" />
      </div>
      <show-info :left-image="['../public/xiaomi/bigMix.webp']" :all="bigData">
        <template #title>手机</template>
      </show-info>

      <show-info
        :left-image="['../public/xiaomi/pro.webp', '../public/xiaomi/minicard.webp']"
        type="min"
        :tabs="tabData"
        :min="{ title: '日常元素抽纸 青春版 24包/箱', price: '29', image: '../public/xiaomi/size2.webp' }"
      >
        <template #title>家电</template>
      </show-info>

      <show-info
        :left-image="['../public/xiaomi/zn1.webp', '../public/xiaomi/zn2.webp']"
        type="min"
        :tabs="zn"
        :min="{ title: '日常元素抽纸 青春版 24包/箱', price: '29', image: '../public/xiaomi/size2.webp' }"
      >
        <template #title>智能</template>
      </show-info>

      <div class="home-banner-box">
        <img src="../public/xiaomi/b.webp" alt="" />
      </div>
    </div>
  </div>
  <div style="background: #fff">
    <div style="width: 1226px; margin: 0 auto">
      <footer-navigation-bar></footer-navigation-bar>
    </div>
  </div>

  <div style="background-color: #f5f5f5">
    <div style="width: 1226px; margin: 0 auto">
      <site-info />
    </div>
  </div>
</template>

<script lang="ts" setup>
import NavigationBar from './components/NavigationBar.vue'
import LogoNavBar from './components/LogoNavBar.vue'
import PictureNavigation from './components/PictureNavigation.vue'
import ShowInfo from './components/ShowInfo.vue'
import { ref } from '@vue/reactivity'
import FooterNavigationBar from './components/FooterNavigationBar.vue'
import SiteInfo from './components/SiteInfo.vue'
const tabData = ref([
  {
    title: '热门',
    data: Array(7).fill({ image: '../public/xiaomi/cardxiaomi.webp', title: 'Xiaomi civi', price: '2599', desc: 'xiaomi civi' }),
    min: { title: '日常元素抽纸 青春版 24包/箱', price: '29', image: '../public/xiaomi/size2.webp' },
  },
  {
    title: '电视影音',
    data: [{ image: '../public/xiaomi/cardxiaomi.webp', title: 'Xiaomi civi', price: '2599', desc: 'xiaomi civi 2' }],
    min: { title: '日常元素抽纸 青春版 24包/箱', price: '29', image: '../public/xiaomi/size2.webp' },
  },
])

const zn = ref([
  {
    title: '热门',
    data: Array(7).fill({ image: '../public/xiaomi/znhot.webp', title: 'Xiaomi Sound', price: '499', desc: '小米高保真智能音箱' }),
    min: { title: '日常元素抽纸 青春版 24包/箱', price: '29', image: '../public/xiaomi/size2.webp' },
  },
  {
    title: '安防',
    data: Array(7).fill({
      image: '../public/xiaomi/znaf.webp',
      title: '小米全自动智能门锁',
      price: '1799',
      desc: '高端全自动，一触即开门',
    }),
    min: { title: '小米室外摄像机 电池版', price: '349', image: '../public/xiaomi/znanmin.webp' },
  },
  {
    title: '出行',
    data: Array(7).fill({ image: '../public/xiaomi/zncx.jpg', title: '九号平衡车', price: '2199', desc: '年轻人的酷玩具' }),
    min: { title: '小米行李箱', image: '../public/xiaomi/znxlx.webp', price: '199' },
  },
])

const bigData = Array(8).fill({ image: '../public/xiaomi/cardxiaomi.webp', title: 'Xiaomi civi', price: '2599', desc: 'xiaomi civi' })
</script>
<style lang="less">
main {
  width: 1226px;
  margin: 0 auto;
}

.page-main {
  background-color: #f5f5f5;
  padding-bottom: 22px;
  .main {
    width: 1226px;
    margin: 0 auto;
    .home-banner-box {
      height: 120px;
      margin: 22px 0;
      overflow: hidden;
      img {
        width: 1226px;
        aspect-ratio: auto 1226 / 120;
        height: 120px;
        border: 0;
      }
    }
  }
}
</style>
