<template>
  <div class="nav">
    <div class="main">
      <template v-for="(item, i) in navs" :key="i">
        <a href="#">{{ item }}</a>
        <span class="sep" v-if="i === navs.length - 1 ? false : true">|</span>
      </template>

      <div class="top-cart">
        <Icon size="20">
          <Cart></Cart>
        </Icon>
        <span>购物车（0）</span>
      </div>

      <div class="right">
        <a href="#">登录</a>
        <span class="sep">|</span>
        <a href="#">注册</a>
        <span class="sep">|</span>
        <a href="#">消息通知</a>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { Cart } from '@vicons/ionicons5'
import { Icon } from '@vicons/utils'

const navs = '小米商城|MIUI|IoT|云服务|天星数科|有品|小爱开放平台|企业团购|资质证照|协议规则|下载app|智能生活|Select Location'.split('|')
</script>

<style lang="less" scoped>
.nav {
  // width: 100vw;
  height: 40px;
  font-size: 12px;
  color: #b0b0b0;
  background-color: #333;
  display: flex;
  position: relative;
  z-index: 9999;
  div.main {
    width: 1226px;
    height: 100%;
    margin: 0 auto;
    line-height: 40px;
    a {
      text-decoration: none;
      color: #b0b0b0;
      &:hover {
        color: white;
      }
    }
    .sep {
      margin: 0 0.3em;
      color: #424242;
    }

    .right {
      float: right;
    }
    .top-cart {
      padding: 0 10px;
      margin-left: 15px;
      float: right;
      color: #b0b0b0;
      background: #424242;
      display: flex;
      align-content: flex-start;
      justify-content: center;
      overflow: hidden;
      .xicon {
        display: block;
        line-height: 45px;
      }
    }
  }
}
</style>
