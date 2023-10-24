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
