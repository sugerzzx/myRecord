# Title

## API

### animationend 事件

监听动画结束事件，在动画结束后执行回调

```js
element.addEventListener("animationend", event => {
  // ...
});
```

### animationstart 事件

监听动画开始事件

```js
element.addEventListener("animationstart", event => {
  // ...
});
```

### animationiteration 事件

监听动画重复事件

```js
element.addEventListener("animationiteration", event => {
  // ...
});
```

### Vue2transition 组件

#### transition 组件的 JavaScript 钩子函数

利用 transition 组件的 JavaScript 钩子函数，可以监听动画的开始、结束、重复事件

### Intersection Observer API

提供了一种异步检测目标元素与祖先元素或 viewport 相交情况变化的方法。

```js
const observer = new IntersectionObserver(callback, options);
observer.observe(element);
```

### requestAnimationFrame 方法

requestAnimationFrame() 方法告诉浏览器您希望执行动画并请求浏览器在下一次重绘之前调用指定的函数来更新动画。该方法使用一个回调函数作为参数，这个回调函数会在浏览器重绘之前调用。

```js
window.requestAnimationFrame(callback);
```

### Web Animations API

Web Animations API 提供了一种控制 CSS 和 SVG 动画的方法，这些动画可以直接在浏览器中使用，无需任何插件或 JavaScript 库。

```js
const player = element.animate(keyframes, options);
```

### Page Visibility API

Page Visibility API 可以用来检测页面是否可见，以及页面是否被用户停留在后台标签页或者最小化窗口中。

```js
document.addEventListener("visibilitychange", () => {
  if (document.hidden) {
    // ...
  } else {
    // ...
  }
});
```
