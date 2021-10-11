<template>
  <nav>
    <a href="#" v-for="(item, i) in navs" :key="i">
      <Icon size="34">
        <component :is="item.icon"></component>
      </Icon>
      <span>{{ item.title }}</span>
    </a>
  </nav>

  <div class="footer-links">
    <dl v-for="i in 5" :key="i">
      <dt>帮助中心</dt>
      <dt><a href="#">账户管理</a></dt>
      <dt><a href="#">购物指南</a></dt>
      <dt><a href="#">订单操作</a></dt>
    </dl>

    <div>
      <span>400-100-5678</span>
      <span>8:00-18:00（仅收市话费）</span>
      <a class="btn">
        <Icon size="14">
          <ChatboxEllipsesOutline />
        </Icon>
        <span>人工客服</span>
      </a>
      <div class="follow">
        <small>关注小米：</small>
        <Icon size="20">
          <LogoWechat />
        </Icon>
        <Icon size="20">
          <LogoWechat />
        </Icon>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { Icon } from '@vicons/utils'
import { StorefrontOutline, WalletOutline, WaterOutline, ChatboxEllipsesOutline, LogoWechat } from '@vicons/ionicons5'
const navs = [
  { title: '预约维修服务', icon: WalletOutline },
  { title: '7天无理由退货', icon: StorefrontOutline },
  { title: '15天免费换货满', icon: ChatboxEllipsesOutline },
  { title: '69包邮', icon: WaterOutline },
  { title: '520余家售后网点', icon: WalletOutline },
]
</script>

<style lang="less" scoped>
nav {
  height: 80px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-bottom: 1px solid #e0e0e0;
  a {
    width: 19.8%;
    color: #616161;
    font-size: 16px;
    text-decoration: none;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all 0.2s linear;
    text-align: center;
    border-right: 1px solid #e0e0e0;
    &:hover {
      color: #ff6700;
    }
    &:last-of-type {
      border-right: none;
    }
    span {
      &:nth-of-type(2) {
        margin-left: 10px;
      }
    }
  }
}

.footer-links {
  display: flex;
  justify-content: space-between;
  margin: 40px 0;
  div {
    width: 247px;
    border-left: 1px solid #e0e0e0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    span {
      &:nth-child(1) {
        margin: 0 0 5px 0;
        font-size: 22px;
        line-height: 1;
        color: #ff6700;
      }
      &:nth-child(2) {
        font-size: 12px;
        line-height: 1;
        margin: 0 0 5px 0;
      }
    }
    .btn {
      width: 120px;
      height: 30px;
      display: flex;
      justify-content: center;
      align-items: center;
      border: 1px solid #ff6700;
      transition: all 0.2s;
      cursor: pointer;
      span {
        margin: 0;
        color: #ff6700;
      }
      &:hover {
        background-color: #ff6700;
      }

      &:hover span {
        color: white;
      }
    }

    .follow {
      font-size: 12px;
      margin-top: 10px;
      color: #616161;
      flex-direction: row;
      span {
        width: 20px;
        height: 20px;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 0 6px 0 0;
      }
    }
  }
  dl {
    dt {
      margin-top: 10px;
      &:first-of-type {
        color: #424242;
        line-height: 1.25;
        font-size: 14px;
      }

      a {
        color: #757575;
        text-decoration: none;
        font-size: 12px;
        transition: all 0.2s;
        &:hover {
          color: #ff6700;
        }
      }
    }
  }
}
</style>
