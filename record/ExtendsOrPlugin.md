# Ecahrts

## 1. 安装 Echarts

```shell
npm install echarts --save
```

## 2. 使用 Echarts

[略](https://echarts.apache.org/handbook/zh/get-started/)

## 3. [Vue-ECharts 插件](https://github.com/ecomfe/vue-echarts/blob/main/README.zh-Hans.md)

这个插件可以让我们在 Vue 中更方便的使用 Echarts，使你的 Echarts 与 Vue 的响应式机制结合起来。

---

# Swiper

## 1. 安装 Swiper

_Vue2 中使用的是 vue-awesome-swiper@4.1.1_

```shell
npm install vue-awesome-swiper@4 --save
```

## 2. 在 Vue 中使用 Swiper

> 这是一个带有分页器的 Swiper

```html
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

---

# Sass

## 1. 安装 Sass

### 1.1 Vue 中安装

```shell
npm install sass-loader sass --save-dev
```

> 由于 VueCLi 无法识别 sass 语法，所以需要安装 sass-loader 和 sass
> 由于 sass 只作为开发依赖，所以使用--save-dev

### 1.2 React 中安装

```shell
npm install sass  --save-dev
```

> 由于 React 可以识别 sass 语法，所以只需要安装 sass 即可

## 2. 使用 Sass

- 首先在 style 标签中添加 lang 属性

  ```scss
  <style lang="scss"> // 这里就可以使用 scss 语法了
  ···
  </style>
  ```

- 嵌套

  ```scss
  <style lang="scss">
  div {
    color: red;
    span {
      color: blue;
    }
  }
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

- 循环

  ```scss
  <style lang="scss">
  @for $i from 1 through 3 {
    .item-#{$i} { width: 2em * $i; }
  }
  </style>
  ```

- ...

  [更多语法](https://sass-lang.com/documentation/)

---

# [Less](https://less.bootcss.com/)

---

# Nprogress

**在隔壁的 [VueRouter.md](./VUE/VueRouter.md) 中**

---

# Mockjs（生成随机数据，拦截 Ajax 请求）

## 1. 安装 Mockjs

```shell
npm install mockjs --save-dev
```

## 2. 使用 Mockjs

- 在 src 目录下新建 mock 目录，然后在 mock 目录下新建 mock.js 文件

  ```js
  // 导入 Mockjs
  import Mock from "mockjs";

  // 使用 Mockjs 模拟数据
  Mock.mock("/api/data", {
    data: {
      "list|10": [
        {
          "id|+1": 1,
          name: "@cname",
          "age|18-28": 25,
          address: "@county(true)",
        },
      ],
    },
  });
  ```

- 在 main.js 中导入 mock.js

  ```js
  import "./mock/mock.js";
  ```

- 在需要使用数据的组件中使用 axios 请求数据

  ```js
  axios.get("/api/data").then(res => {
    console.log(res.data);
  });
  ```

3. 更多 Mockjs 语法

[Mockjs 官网](http://mockjs.com/examples.html)

# Dotenv

## 1. 使用 dotenv(ts)

- 安装 dotenv

  ```shell
  npm install dotenv @types/dotenv --save-dev
  ```

- 在项目根目录下新建 .env 文件

  ```shell
  # .env
  APP_BASE_URL = http://localhost:8080
  ```

- 在 src/config/config.ts 中导入 dotenv

  ```ts
  import dotenv from "dotenv";

  dotenv.config();

  export default {
    baseUrl: process.env.APP_BASE_URL,
  };
  ```

- 在 main.ts 中使用环境变量

  ```ts
  import config from "./config/config";

  console.log(config.baseUrl); // http://localhost:8080
  ```
