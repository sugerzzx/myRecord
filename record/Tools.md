# Ecahrts

## 1. VueCli 中安装 Echarts

```shell
npm install echarts --save
```

## 2. 在 VueCli 中使用 Echarts

[略](https://echarts.apache.org/handbook/zh/get-started/)

# Swiper

## 1. VueCli 中安装 Swiper

> Vue2 中使用的是 vue-awesome-swiper@4.1.1

```shell
npm install vue-awesome-swiper@4 --save
```

## 2. 在 Vue 中使用 Swiper

> 这是一个带有分页器的 Swiper

```vue
<template>
  <!-- options 为 Swiper 的配置项 -->
  <swiper class="swiper" :options="swiperOption">
    <swiper-slide>Slide 1</swiper-slide>
    <swiper-slide>Slide 2</swiper-slide>
    <swiper-slide>Slide 3</swiper-slide>
    <swiper-slide>Slide 4</swiper-slide>
    <swiper-slide>Slide 5</swiper-slide>
    <swiper-slide>Slide 6</swiper-slide>
    <swiper-slide>Slide 7</swiper-slide>
    <swiper-slide>Slide 8</swiper-slide>
    <swiper-slide>Slide 9</swiper-slide>
    <swiper-slide>Slide 10</swiper-slide>
    <div class="swiper-pagination" slot="pagination"></div>
  </swiper>
</template>

<script>
// 导入 Swiper, SwiperSlide 组件
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
// 导入 Swiper 样式
import "swiper/css/swiper.css";

export default {
  name: "swiper-example-pagination",
  title: "Pagination",
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      swiperOption: {
        // Swiper 的配置项,pagination 为分页器
        pagination: {
          // el 为分页器的容器
          el: ".swiper-pagination",
        },
      },
    };
  },
};
</script>

<style lang="scss" scoped>
@import "./base.scss";
</style>
```

[更多例子](https://v1.github.surmon.me/vue-awesome-swiper/)

# Sass

## 1. VueCli 中安装 Sass

```shell
npm install sass-loader sass --save-dev
```

> 由于 VueCLi 无法识别 sass 语法，所以需要安装 sass-loader 和 sass
> 由于 sass 只作为开发依赖，所以使用--save-dev

## 2. 在 VueCli 中使用 Sass

- 首先在 style 标签中添加 lang 属性

  ```scss
  <style lang="scss"> // 这里就可以使用 scss 语法了
  ···
  </style>
  ```

- 定义变量和使用变量

  ```scss
  <style lang="scss">
  // 定义变量
  $color: #114514;
  // 使用变量
  div {
    color: $color;
  }
  </style>
  ```

# Less

## 1. VueCli 中安装 Less

```shell
npm install less-loader less --save-dev
```

## 2. 在 VueCli 中使用 Less

- 首先在 style 标签中添加 lang 属性

```scss
<style lang="less"> // 这里就可以使用 less 语法了
···
</style>
```

- 定义变量和使用变量

```scss
<style lang="less">
// 定义变量
@color: #114514;
// 使用变量
div {
  color: @color;
}
</style>
```

# Nprogress

**在隔壁的 [VueRouter.md](./LearningVueRouter.md) 中**

# Mockjs
