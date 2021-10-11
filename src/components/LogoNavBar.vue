<template>
  <div style="position: relative; z-index: 10000">
    <div class="container">
      <div class="logo"></div>
      <div class="nav">
        <template v-for="(item, i) in navs" :key="i">
          <a
            href="#"
            v-if="i == navs.length - 1 || i == navs.length - 2 ? false : true"
            @mousemove="move(i)"
            @mouseout="theme.ptop = '-200px'"
          >
            {{ item }}</a
          >
          <a href="#" v-if="i == navs.length - 1 || i == navs.length - 2 ? true : false">{{ item }}</a>
        </template>
      </div>
      <div class="search">
        <div class="box">
          <input type="text" placeholder="手机" />
          <div class="submi-btn">
            <Icon size="30">
              <Search></Search>
            </Icon>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="line" @mousemove="move()" @mouseout="theme.ptop = '-200px'" v-show="theme.ptop == '-200px' ? false : true"></div>
  <div
    class="card"
    :style="{ boxShadow: theme.ptop == '-200px' ? 'none' : '0px 2px 2px rgba(0, 0, 0, 0.2)' }"
    @mousemove="move()"
    @mouseout="theme.ptop = '-200px'"
  >
    <div class="container">
      <ul>
        <li v-for="item in xiaomiData" :key="item.id">
          <a href="#">
            <div>
              <!-- <img src="../assets/xiaomi/8cad77bda138fd94eadbc2ddfced7c56.webp" alt="xiaomi" width="160" height="110" /> -->
              <img :src="item.img" alt="xiaomi" width="160" height="110" />
            </div>
            <span>{{ item.name }}</span>
            <span>{{ item.price }}</span>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { Icon } from '@vicons/utils'
import { Search } from '@vicons/ionicons5'
import { reactive, ref } from '@vue/reactivity'
import xiaomi1 from '../../public/xiaomi/8cad77bda138fd94eadbc2ddfced7c56.webp'
import xiaomi2 from '../../public/xiaomi/087c52d253d9301dff7743d6bf2d0330.webp'
import k40g from '../../public/xiaomi/k40g.webp'
import redmi10 from '../../public/xiaomi/redmi10.webp'
const navs = '小米手机|Redmi|红米|电视|笔记本|平板|家电|路由器|智能硬件服务|社区'.split('|')
const theme = reactive({
  ptop: '-200px',
  borderBottom: 'none',
})

const index = ref(0)

const res = [
  [
    {
      id: 1,
      img: xiaomi1,
      name: 'Xaiomi Civi',
      price: '2599元起',
    },
    {
      id: 2,
      img: xiaomi2,
      name: 'Xaiomi MIX4',
      price: '4999元起',
    },
  ],
  [
    {
      id: 1,
      img: redmi10,
      name: 'Redmi Note 10',
      price: '1599元起',
    },
    {
      id: 2,
      img: k40g,
      name: 'Redmi K40 游戏版',
      price: '1999元起',
    },
    {
      id: 3,
      img: xiaomi1,
      name: 'Xaiomi Civi',
      price: '2599元起',
    },
  ],
]
const xiaomiData = ref([...res[0]])
const move = (i: number = index.value) => {
  index.value = i
  theme.ptop = '140px'
  theme.borderBottom = '1px solid #ccc'
  if (i > 1) i = 0
  xiaomiData.value = res[i]
}
</script>

<style lang="less" scoped>
* {
  box-sizing: border-box;
}
.container {
  width: 1226px;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-sizing: border-box;
  z-index: 100;
  background-color: white;
  position: relative;
  margin: 0 auto;
  .logo {
    width: 56px;
    height: 56px;
    background: url('../assets/logo-mi2.png') no-repeat;
    background-size: 56px;
  }
  .nav {
    height: 100%;
    margin-left: 140px;
    display: flex;
    align-items: center;
    box-sizing: border-box;
    a {
      height: 100%;
      font-size: 16px;
      color: #333;
      text-decoration: none;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 26px 10px 38px;
      &:hover {
        color: #ff6700;
      }
    }
  }

  .search {
    width: 300px;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: flex-end;

    .box {
      width: 300px;
      display: flex;
      height: 50px;
      border: 1px solid #e0e0e0;
      transition: all 0.3s;
      border-radius: 2px;
      flex: 1;
      &:hover {
        border-color: #b0b0b0;
      }
      &:hover .submi-btn {
        border-color: #b0b0b0;
      }
      input {
        width: 100%;
        border: none;
        outline: none;
        padding: 0 8px;
      }
      .submi-btn {
        // height: 100%;
        padding: 10px;
        border-left: 1px solid #e0e0e0;
        transition: all 0.3s;
        display: flex;
        align-items: center;
        color: #616161;

        &:hover {
          // border-radius: 2px;
          background-color: #ff6700;
          color: white;
        }
      }
    }
  }
}

.line {
  width: 100%;
  height: 1px;
  position: absolute;
  left: 0;
  z-index: 9999;
  border-bottom: v-bind('theme.borderBottom');
}

.card {
  width: 100%;
  height: 230px;
  box-sizing: border-box;
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.2);
  display: flex;
  align-items: center;
  position: absolute;
  top: v-bind('theme.ptop');
  left: 0;
  background-color: white;
  z-index: 90;
  transition: top 0.3s;
  .container {
    width: 1226px;
    height: 100%;
    margin: 0 auto;
    ul {
      display: flex;
      list-style: none;
      padding: 0;
      li {
        a {
          display: flex;
          flex-direction: column;
          font-size: 12px;
          text-decoration: none;
        }
        span {
          text-align: center;
          line-height: 20px;
          &:nth-of-type(1) {
            color: #333;
          }
          &:nth-of-type(2) {
            color: #ff6700;
          }
        }
      }
    }
  }
}
</style>
