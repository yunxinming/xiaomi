<template>
  <div class="title">
    <h2>
      <slot name="title"></slot>
    </h2>
    <div class="more">
      <a href="#" v-if="props.tabs?.length == undefined">
        查看更多
        <Icon size="14">
          <ChevronForwardCircleOutline />
        </Icon>
      </a>
      <ul v-else>
        <li :class="{ active: active == index }" v-for="(item, index) in props.tabs" :key="index" @mousemove="active = index">
          {{ item.title }}
        </li>
      </ul>
    </div>
  </div>
  <main>
    <commodity-card big :image="props.leftImage![0]" v-if="props.type == 'max'" />
    <div v-else>
      <commodity-card v-for="(item, i) in props.leftImage" :key="i" :image="item" />
    </div>
    <div class="right" v-if="props.tabs?.length! >= 2">
      <div class="info" v-for="(item, i) in props.tabs![active].data" :key="i">
        <commodity-card :image="item.image" :title="item.title" :desc="item.desc" :price="item.price" />
      </div>
      <div class="info">
        <commodity-card
          :image="props.tabs![active].min?.image"
          type="min"
          :title="props.tabs![active].min?.title"
          :price="props.tabs![active].min?.price"
        ></commodity-card>
      </div>
    </div>
    <div class="right" v-else>
      <div class="info" v-for="(item, i) in props.all" :key="i">
        <commodity-card :image="item.image" :title="item.title" :desc="item.desc" :price="item.price" />
      </div>
    </div>
  </main>
</template>

<script lang="ts" setup>
import CommodityCard from './CommodityCard.vue'
import { ChevronForwardCircleOutline } from '@vicons/ionicons5'
import { Icon } from '@vicons/utils'
import { ref } from '@vue/reactivity'

const props = withDefaults(
  defineProps<{
    tabs?: Array<{ title: string; data: any; min?: { image: string; title: string; price: string | number } }>
    type?: 'min' | 'max'
    leftImage?: Array<string>
    min?: { image: string; title: string; price: string | number }
    all?: Array<any>
  }>(),
  {
    type: 'max',
  }
)
const active = ref(0)
</script>

<style lang="less" scoped>
.title {
  height: 55px;
  display: flex;
  box-sizing: border-box;
  justify-content: space-between;
  align-items: center;
  h2 {
    margin: 0;
    font-size: 22px;
    font-weight: 200;
    line-height: 58px;
    color: #333;
  }
  .more {
    a {
      display: flex;
      justify-content: center;
      align-items: center;
      text-decoration: none;
      color: #333;
      transition: all 0.2s linear;
      span {
        margin-left: 2px;
      }

      &:hover {
        color: #ff6700;
      }
    }

    ul {
      padding: 0;
      list-style: none;
      color: #333;
      display: flex;
      li {
        height: 24px;
        display: block;
        cursor: pointer;
        margin-left: 30px;
        font-size: 16px;
      }
    }

    .active {
      color: #ff6700;
      border-bottom: 2px solid #ff6700;
    }
  }
}

main {
  height: 628px;
  display: flex;
  flex-wrap: wrap;

  .right {
    width: 1226-234px;
    display: flex;
    flex-wrap: wrap;
    .info {
      height: 300px;

      box-sizing: border-box;
      margin-left: 14px;
      // margin-bottom: 14px;
    }
  }
}
</style>
