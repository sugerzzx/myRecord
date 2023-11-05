# ReactNative

## 1. ReactNative 简介

React Native 是 Facebook 开发的一个开源的跨平台移动应用框架。它主要的特点包括:

- 跨平台:使用 React Native 可以只开发一套代码,然后生成 iOS 和 Android 原生应用。
- 声明式 UI:类似 React 在 Web 上的用法,使用声明式的方式来构建应用界面。
- 组件化:提供了一系列可复用的组件,开发者可以通过组合这些组件来构建应用。
- 热重载:支持热重载,可以在不重启应用的情况下加载 JS 代码的修改。
- 原生控制:内置很多原生控件,也可以通过 Bridge 机制调用平台原生能力。
- 灵活与高效:使用 JavaScript 开发可以获得很高的开发效率。底层使用异步机制,性能也很不错。
  React Native 的工作原理是在平台原生 UI 组件和 JavaScript 代码之间建立了一个 Bridge。JavaScript 代码可以调用 Bridge 提供的接口来控制原生组件的布局、样式等,原生组件也可以通过 Bridge 向 JavaScript 发送事件通知。
  ![RN工作原理](../../src/RN//RNWorkPrinciple.png)
