<template>
  <template v-if="props.big">
    <div class="big-card">
      <a href="#">
        <img :src="props.image" alt="" />
      </a>
    </div>
  </template>
  <template v-else-if="props.type == 'min'">
    <div class="min">
      <a href="#">
        <div>
          <p class="title">{{ props.title }}</p>
          <p>{{ props.price }}元</p>
        </div>
        <img :src="props.image" alt="hhh" />
      </a>
      <a href="#">
        <div>
          浏览更多
          <small>热门</small>
        </div>
        <Icon size="58"> <ArrowForwardCircleOutline /> </Icon>
      </a>
    </div>
  </template>
  <template v-else>
    <a href="#" class="card" v-if="props.title != undefined">
      <img :src="props.image" alt="" width="160" height="160" />
      <h3 class="title">{{ props.title }}</h3>
      <p class="desc">{{ props.desc }}</p>
      <p class="price" v-if="props.title">{{ props.price }}起</p>
    </a>
    <a class="min-card" href="#" v-else>
      <img :src="props.image" alt="" width="234" height="300" />
    </a>
  </template>
</template>

<script lang="ts" setup>
import { Icon } from '@vicons/utils'
import { ArrowForwardCircleOutline } from '@vicons/ionicons5'
const props = withDefaults(
  defineProps<{
    image?: string
    big?: boolean
    title?: string
    desc?: string
    price?: string | number
    size?: number | string
    type?: 'min' | 'max'
  }>(),
  {
    big: false,
    size: 0,
  }
)
</script>

<style lang="less" scoped>
.min {
  width: 234px;
  height: 300px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  a {
    height: 143px;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    text-decoration: none;
    background-color: white;
    color: #333;
    transition: all 0.2s linear;
    overflow: hidden;

    &:hover {
      box-shadow: 0 15px 30px rgb(0 0 0 / 10%);
      transform: translate3d(0, -2px, 0);
    }
    &:nth-of-type(1) {
      p {
        margin: 0;
      }
      .title {
        font-size: 14px;
        font-weight: 400;
        padding: 15px 25px 2px 20px;
      }
      p {
        &:nth-of-type(2) {
          color: #ff6700;
          padding: 0 25px 0 20px;
        }
      }
    }
    &:nth-of-type(2) {
      div {
        width: 80px;
        display: flex;
        flex-direction: column;
        margin: 0 50px 0 30px;
        font-size: 18px;
        color: #333;
        small {
          display: block;
          font-size: 12px;
          color: #757575;
          margin-top: 5px;
        }
      }
      span {
        flex: 1;
        align-items: center;
        justify-content: center;
        color: #ff6700;
      }
    }
    img {
      width: 80px;
      height: 80px;
      border: 0;
    }
  }
}

.big-card {
  width: 234px;
  height: 614px;
  transition: all 0.2s linear;
  overflow: hidden;

  &:hover {
    box-shadow: 0 15px 30px rgb(0 0 0 / 10%);
    transform: translate3d(0, -2px, 0);
  }
  a {
    transition: all 0.2s linear;
    img {
      height: 641px;
    }
  }
}

.min-card {
  width: 234px;
  height: 300px;
  background-color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 13px;
  transition: all 0.2s linear;
  &:hover {
    box-shadow: 0 15px 30px rgb(0 0 0 / 10%);
    transform: translate3d(0, -2px, 0);
  }
}
.card {
  width: 234px;
  height: 300px;
  background-color: white;
  padding: 20px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-sizing: border-box;
  text-decoration: none;
  transition: all 0.2s linear;
  &:hover {
    box-shadow: 0 15px 30px rgb(0 0 0 / 10%);
    transform: translate3d(0, -2px, 0);
  }
  .title {
    text-align: center;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    font-size: 14px;
    font-weight: 400;
    color: #333;
    margin-top: 0;
    margin-bottom: 2px;
  }
  img {
    margin-bottom: 16px;
  }
  p {
    margin: 0;
  }

  .desc {
    height: 18px;
    line-height: 18px;
    font-size: 12px;
    color: #b0b0b0;
    margin-bottom: 10px;
  }
  .price {
    color: #ff6700;
  }
}
</style>
