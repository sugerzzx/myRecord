# Window 对象

## Window 对象介绍

window 对象表示一个包含 DOM 文档的窗口，其 document 属性指向窗口中载入的 DOM 文档 。

Window 接口是各种函数、命名空间、对象和构造函数的家

## Window.postMessage()

postMessage 接口允许窗口之间相互通信，无论它们来自什么源。

因此，这是解决“同源”策略的方式之一。它允许来自于 john-smith.com 的窗口与来自于 gmail.com 的窗口进行通信，并交换信息，但前提是它们双方必须均同意并调用相应的 JavaScript 函数。这可以保护用户的安全。

这个接口有两个部分。

```js
otherWindow.postMessage(message, targetOrigin, [transfer]);
```
