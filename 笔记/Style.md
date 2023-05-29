<!-- 常用CSS样式收集 -->

# 媒体查询适应字体

```css
/* 超小型设备（电话，600px 及以下） */
@media only screen and (max-width: 600px) {
  html {
    font-size: 16px;
  }
}

/* 小型设备（纵向平板电脑和大型手机，600 像素及以上） */
@media only screen and (min-width: 600px) {
  html {
    font-size: 24px;
  }
}

/* 中型设备（横向平板电脑，768 像素及以上） */
@media only screen and (min-width: 768px) {
  html {
    font-size: 30px;
  }
}

/* 大型设备（笔记本电脑/台式机，992px 及以上） */
@media only screen and (min-width: 992px) {
  html {
    font-size: 40px;
  }
}

/* 超大型设备（大型笔记本电脑和台式机，1200px 及以上） */
@media only screen and (min-width: 1200px) {
  html {
    font-size: 40px;
  }
}
```
