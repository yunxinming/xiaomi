<template>
  <div class="container">
    <div class="left">
      <ul>
        <li v-for="(item, index) in data" :key="index" @mousemove="choose = index" @mouseout="choose = -1">
          <span>{{ item.title }}</span>
          <Icon size="20">
            <ChevronForwardOutline />
          </Icon>

          <div v-show="index == choose ? true : false">
            <a href="#" v-for="(data, i) in item.data" :key="i">
              <img :src="data.image" alt="xiaomi civi" width="40" height="40" />
              <span>{{ data.title }}</span>
            </a>
          </div>
        </li>
      </ul>
    </div>

    <swiper :navigation="true" :pagination="true" :loop="true" :loopFillGroupWithBlank="true">
      <swiper-slide>
        <img src="../../public/xiaomi/lbt.jpg" width="1226" height="460" />
      </swiper-slide>
      <swiper-slide>
        <img src="../../public/xiaomi/mix4.webp" width="1226" height="460" />
      </swiper-slide>
    </swiper>
  </div>

  <div class="hero">
    <div class="left">
      <a href="#">
        <img src="../../public/xiaomi/clock.png" alt="保障服务" width="24" height="24" />
        <span>保障服务</span>
      </a>
      <a href="#">
        <img src="../../public/xiaomi/qiye.png" alt="企业团购" width="24" height="24" />
        <span>企业团购</span>
      </a>
      <a href="#">
        <img src="../../public/xiaomi/f.png" alt="F码" width="24" height="24" />
        <span>F码通道</span>
      </a>
      <a href="#">
        <img src="../../public/xiaomi/mif.png" alt="米粉卡" width="24" height="24" />
        <span>米粉卡</span>
      </a>
      <a href="#">
        <img src="../../public/xiaomi/huanxin.png" alt="换新服务" width="24" height="24" />
        <span>以旧换新</span>
      </a>
      <a href="#">
        <img src="../../public/xiaomi/chongzhi.png" alt="话费充值" width="24" height="24" />
        <span>话费充值</span>
      </a>
    </div>
    <div class="right">
      <a href="#">
        <img src="../../public/xiaomi/big.jpg" alt="xiaomi" />
      </a>
      <a href="#">
        <img src="../../public/xiaomi/big2.jpg" alt="xiaomi" />
      </a>
      <a href="#">
        <img src="../../public/xiaomi/big3.png" alt="xiaomi" />
      </a>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ChevronForwardOutline } from '@vicons/ionicons5'
import { Icon } from '@vicons/utils'
import { Swiper, SwiperSlide } from 'swiper/vue'
import SwiperCore, { Navigation, Pagination } from 'swiper'

import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'
import { ref } from '@vue/reactivity'

import img from '../../public/xiaomi/civi.webp'

SwiperCore.use([Navigation, Pagination])
const choose = ref(-1)
const data = ref([
  {
    title: '手机',
    data: [
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
      { title: '小米 Civi', image: img },
    ],
  },
  {
    title: '电视',
    data: [{ title: '小米 Civi2', image: img }],
  },
  {
    title: '笔记本 平板',
    data: [{ title: '小米 Civi3', image: img }],
  },
  {
    title: '家电',
    data: [{ title: '小米 Civi4', image: img }],
  },
  {
    title: '出行 穿戴',
    data: [{ title: '小米 Civi5', image: img }],
  },
  {
    title: '智能 路由器',
    data: [{ title: '小米 Civi6', image: img }],
  },
  {
    title: '电源 配件',
    data: [{ title: '小米 Civi7', image: img }],
  },
  {
    title: '健康 儿童',
    data: [{ title: '小米 Civi8', image: img }],
  },
  {
    title: '耳机 音响',
    data: [{ title: '小米 Civi9', image: img }],
  },
  {
    title: '生活 箱包',
    data: [{ title: '小米 Civi10', image: img }],
  },
])
</script>

<style lang="less" scoped>
.container {
  width: 1226px;
  height: 460px;
  margin: 0 auto;
  position: relative;

  .left {
    width: 234px;
    height: 460px;
    background-color: rgba(105, 101, 101, 0.6);
    position: absolute;
    top: 0;
    left: 0;
    z-index: 19;
    padding: 20px 0;
    box-sizing: border-box;
    ul {
      margin: 0;
      padding: 0;
      list-style: none;

      li {
        height: 42px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding-left: 30px;
        &:hover {
          background-color: #ff6700;
        }
        span {
          color: white;
          &:nth-of-type(2) {
            margin-right: 10px;
          }
        }

        div {
          width: 1226-234px;
          height: 100%;
          position: absolute;
          top: 0;
          left: 234px;
          background-color: white;
          display: flex;
          flex-direction: column;
          flex-wrap: wrap;
          align-content: flex-start;
          border-top: 1px solid rgba(0, 0, 0, 0.1);
          box-shadow: 1px 3px 7px rgba(0, 0, 0, 0.1);
          img {
            margin-right: 10px;
          }
          a {
            width: 265px;
            height: 76px;
            display: flex;
            align-items: center;
            box-sizing: border-box;
            text-decoration: none;
            padding: 18px 20px;

            span {
              width: 172px;
              color: #333;
              text-overflow: ellipsis;
              overflow: hidden;
              font-size: 14px;
              &:hover {
                color: #ff6700;
              }
            }
          }
        }
      }
    }
  }

  &:deep(.swiper) {
    width: 1226px;
    height: 460px;
    z-index: 10 !important;
  }

  &:deep(.swiper-button-prev) {
    width: 41px;
    height: 69px;
    left: 234px;
    color: #ccc;
    &:hover {
      background-color: #ccc;
      color: white;
    }
    &::after {
      font-size: 28px;
    }
  }

  &:deep(.swiper-button-next) {
    width: 41px;
    height: 69px;
    right: 1px;
    color: #ccc;
    &:hover {
      background-color: #ccc;
      color: white;
    }
    &::after {
      font-size: 28px;
    }
  }

  // &:deep(.swiper-pagination-horizontal) {
  // }
  .right {
    width: 234px;
    height: 460px;
  }
}

.hero {
  display: flex;
  margin-top: 14px;
  .left {
    width: 234px;
    height: 170px;
    background-color: #5f5750;
    display: flex;
    flex-wrap: wrap;
    box-sizing: border-box;
    padding: 3px;
    a {
      width: 76px;
      height: 82px;
      box-sizing: border-box;
      font-size: 12px;
      color: #928c87;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      text-decoration: none;
      border-right: 1px solid #665e57;
      border-bottom: 1px solid #665e57;
      &:nth-of-type(4),
      &:nth-of-type(5),
      &:nth-of-type(6) {
        border-bottom: none;
      }

      &:nth-of-type(3),
      &:nth-of-type(6) {
        border-right: none;
      }

      &:hover span {
        color: white;
      }
      span {
        margin-top: 5px;
      }
    }
  }

  .right {
    display: flex;
    box-sizing: border-box;
    a {
      margin-left: 15px;
      transition: all 0.3s;
      &:nth-of-type(1) {
        margin-left: 14px;
      }
      &:hover {
        -webkit-box-shadow: 0 15px 30px rgb(0 0 0 / 10%);
        box-shadow: 0 15px 30px rgb(0 0 0/10%);
      }
      img {
        display: block;
        width: 316px;
        height: 170px;
      }
    }
  }
}
</style>
