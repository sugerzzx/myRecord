<!-- 施工中 -->

# HTML

## 1.SGML：标准通用标记语言

> SGML 代表**标准通用标记语言**(_Standard Generalized Markup Language_)。定义了创建标准标记语言的规则，它为 HTML、XML 等标记语言奠定了基础，其本身不是一种标记语言。XML、HTML 都是 SGML 的子集、具体应用。

1. SGML 是一种标准通用标记语言，用于定义 XML、HTML 等标记语言的语法规则。
2. 它定义了符号< >包围的标签、不同类型的标签、属性等的书写规范。
3. SGML 本身不是一种标记语言，而是为标记语言定义语法的元语言。
4. XML 和 HTML 都是 SGML 的子集和具体应用。

> HTML5 属于 SGML 的扩展和演变，但已经不再严格遵照 SGML 的复杂语法要求，而是沿用 SGML 的基本思想,根据网络环境的变化进行了简化和创新。

## 2.DTD：文档类型定义

> DTD 代表**文档类型定义**(_Document Type Definition_)。DTD 规定了 XML 或 HTML 的特定版本中允许的元素、属性和实体。DTD 可以在文档中直接声明，也可以引用外部的 DTD 文件。

> HTML4.01 时代还使用 DTD 进行语法约束,在 HTML5 中则放弃了 DTD,改用简单的<!DOCTYPE html>声明代替。

## 3.DOCTYPE 的作用是什么？标准版模式与兼容模式有什么区别？

```html
<!DOCTYPE html>
```

> DOCTYPE 声明位于文档中的最前面，处于 html 标签之前，声明文档的类型和 DTD 规范，告知浏览器的解析器用什么文档标准解析这个文档，以使浏览器切换到相应的渲染模式。

- 声明文档类型，使浏览器选择相应的渲染模式。
- 在 HTML 4.01 时代，doctype 还链接到 DTD 文件以对文档进行语法校验。

## 4. HTML5 为什么只需要写`<!DOCTYPE html>`？

> HTML5 已经不完全基于 SGML，因此不需要对 DTD 进行引用，但是需要 doctype 来规范浏览器的行为。

## 5. 行内元素有哪些？块级元素有哪些？ 空元素有哪些？

1. 行内元素：a、b、span、img、input、strong、select、label、em、button、textarea
2. 块级元素：div、ul、li、dl、dt、dd、p、h1-h6、blockquote
3. 空元素：即系没有内容的 HTML 元素，例如：br、meta、hr、link、input、img

## 6.`link`标签和`@import`的区别是？

```html
<link rel="stylesheet" href="style.css" />
<style>
  @import url("style.css");
</style>
```

1. **位置**：`<link>`标签通常放在文档的`<head>`部分，而`@import` 规则需要放在样式表文件的顶部，且必须位于其他样式规则之前。

2. **加载方式**：`<link>`标签会并行地加载样式表，不会阻塞页面的渲染，而`@import` 规则会在样式表文件被加载和解析完毕后再加载其他资源，这可能会导致页面加载速度较慢。

3. **兼容性**：`<link>`标签在所有浏览器中都被支持，而`@import` 规则在较旧的浏览器中可能不被完全支持。

4. **功能扩展**：`<link>`标签具有更多的功能扩展性。通过设置 rel 属性，可以指定样式表的关系类型，例如 `stylesheet` 表示引入样式表，`alternate stylesheet` 表示备选样式表。此外，还可以使用 `media` 属性来指定适用样式表的媒体类型。`@import` 规则相对简单，不能指定关系类型或媒体类型。

## 7. 介绍一下你对浏览器内核的理解？

> 浏览器内核是指浏览器所采用的渲染引擎或排版引擎，用于解析和渲染网页内容。它负责将 HTML、CSS 和 JavaScript 等网页元素转化为可视化的网页布局和交互效果,不同浏览器内核之间的差异主要体现在渲染引擎和 JavaScript 引擎的不同实现和特性上。

内核分为两个部分：渲染引擎和 JS 引擎。

1. **渲染引擎**（_Rendering Engine_）：渲染引擎负责解析 HTML、CSS 和其他相关资源，并将它们渲染为可视化的网页。它处理文档的结构和样式，计算元素的位置和尺寸，处理布局和绘制等任务。渲染引擎决定了网页的外观和交互行为。

   常见的渲染引擎包括：

   - Trident（Internet Explorer）
   - Gecko（Firefox）
   - WebKit（Safari、Chrome、Opera 等）
   - Blink（Chrome、Opera 等）

2. **JavaScript 引擎**（_JavaScript Engine_）：JavaScript 引擎负责解析和执行 JavaScript 代码。它将 JavaScript 代码转换为可执行的机器码，并处理脚本中的变量、函数、循环、条件等逻辑。JavaScript 引擎是实现 JavaScript 语言的核心组件，对网页的交互性和动态效果起着重要作用。

   常见的 JavaScript 引擎包括：

   - V8（Chrome、Node.js 等）
   - SpiderMonkey（Firefox）
   - JavaScriptCore（Safari）

# CSS

# JS

## 1. [数据类型](https://zh.javascript.info/types)

> JavaScript 中有八种基本的数据类型，其中七种是原始类型，另外一种是对象类型。

- 七种原始数据类型：
  - `number` 用于任何类型的数字：整数或浮点数，在 ±(253-1) 范围内的整数。
  - `bigint` 用于任意长度的整数。
  - `string` 用于字符串：一个字符串可以包含 0 个或多个字符，所以没有单独的单字符类型。
  - `boolean` 用于 true 和 false。
  - `null` 用于未知的值 —— 只有一个 null 值的独立类型。
  - `undefined` 用于未定义的值 —— 只有一个 undefined 值的独立类型。
  - `symbol` 用于唯一的标识符。
- 以及一种非原始数据类型：
  - `object` 用于更复杂的数据结构。

**我们可以通过 typeof 运算符查看存储在变量中的数据类型。**

- 通常用作 typeof x，但 typeof(x) 也可行。
- 以字符串的形式返回类型名称，例如 "string"。
- typeof null 会返回 "object" —— 这是 JavaScript 编程语言的一个错误，实际上它并不是一个 object。

## [对象](https://zh.javascript.info/object)

### [深拷贝与浅拷贝](https://zh.javascript.info/object-copy)

> 由于对象是引用类型，所以在拷贝对象时，拷贝的是对象的引用，而不是对象本身。因此，当拷贝的引用类型发生改变时，原对象也会发生改变。

- **浅拷贝**：只拷贝对象的第一层属性，如果属性是基本类型，则拷贝其值，如果属性是引用类型，则拷贝其引用。

  - _浅拷贝的一种实现方式：使用 ES6 的 `Object.assign({},obj1,obj2)` 方法或者扩展运算符 `{...obj}`。_

- **深拷贝**：递归地拷贝对象的所有层级属性，拷贝后的对象与原对象完全隔离，互不影响。

  - _深拷贝的一种实现方式：使用 lodash 的 cloneDeep 方法。_

- **注意**：直接赋值甚至不能被称为拷贝：`obj1 = obj2`。

## [闭包](https://zh.javascript.info/closure#ci-fa-huan-jing)

### 变量作用域

### 词法环境

在 JavaScript 中，每个运行的函数，代码块 `{...}` 以及整个脚本，都有一个被称为 词法环境（Lexical Environment） 的内部（隐藏）的关联对象。

词法环境对象由两部分组成：

1. **环境记录**（Environment Record） —— 一个存储所有局部变量作为其属性（包括一些其他信息，例如 this 的值）的对象。
2. 对 **外部词法环境** 的**引用**，与外部代码相关联。

在创建词法环境时，词法环境虽然会预填充所有变量，但是他们任然处于未初始化状态，即引擎知晓他们的存在，但在使用`let`声明之前，不能引用，但是有一个特例，即函数声明，这也是为什么可以在函数声明之前调用该函数，函数表达式则不行。

### 闭包

- 定义：闭包 是指一个函数可以记住其外部变量并可以访问这些变量。

- 为什么所有函数都是闭包的：所有的函数在“诞生”时都会记住创建它们的词法环境，因为所有函数都有名为 `[[Environment]]` 的隐藏属性。

- 闭包的作用: 1.局部作用域， 防止全局破坏 2.代替全局变量，又和全局变量一样的生存周期. 3.模块化也是闭包.

## [事件循环](https://zh.javascript.info/event-loop)

> 事件循环是 JavaScript 实现异步编程的一种解决方案，它是一个执行模型，用于处理消息队列中的事件。一个 **JavaScript 引擎**在**等待任务**，**执行任务**和**进入休眠状态等待更多任务**这**几个状态之间转换**的**无限循环**。

### 宏任务

> 宏任务是由宿主环境提供的任务，它们的回调函数会被推入消息队列中，等待执行。常见的宏任务包括：

- `setTimeout`、`setInterval`、`setImmediate`（Node.js 环境）等定时器任务。

- `I/O`任务，包括网络请求、文件读写、本地存储等。

- `UI` 渲染任务，包括 DOM 渲染、页面重绘等。

### 微任务

> 微任务是由 JavaScript 自身提供的任务，它们的回调函数会被推入微任务队列中，等待执行。常见的微任务包括：

- `Promise` 的回调函数。

- `MutationObserver` 的回调函数。

- `process.nextTick`（Node.js 环境）。

### 执行顺序

1. 从 宏任务 队列（例如 “script”）中出队（dequeue）并**执行最早的任务**。
2. 执行**所有** 微任务：

   - 当微任务队列非空时：
     - 出队（dequeue）并执行最早的微任务。

3. 如果有变更，则将变更渲染出来。
4. 如果宏任务队列为空，则休眠直到出现宏任务。
5. 转到步骤 1。

# WX

# VUE

## VUE2

### 1. VUE2 响应式原理

已迁移至 Vue 文件夹的 VueReactivity

### 2. v-For 中 key

#### 作用

> 在虚拟 DOM 中，key 会作为节点的标识，用于优化渲染。

#### key 的原理

使用 key 时，当节点的顺序发生变化时，页面不会立即重新渲染，Vue 会基于 key 的变化重新排列元素顺序，并且会移除 key 不存在的元素。如果没有为每个节点提供一个唯一的 key 值，Vue 会使用一种**最大限度减少动态元素**并且尽可能的尝试**就地修改/复用相同类型元素**的算法，即会遍历整个列表，查找需要更新的节点，这样做的效率非常低下。

> 所以在使用 key 的时候不要使用 index，因为 index 代表数组的下标，而当数组的顺序发生变化时，index 也会随之发生变化，这样就会导致节点的顺序发生变化时，会导致页面重新渲染。

### 3. this.$nextTick()

> this.$nextTick() 是 Vue 在更新 DOM 之后异步执行的回调函数，它可以在 DOM 更新后执行一些操作。

- 作用：在下次 DOM 更新循环结束之后执行**延迟回调**，在修改数据之后立即使用这个方法，获取更新后的 DOM。

- 用法：this.$nextTick([callback])

- 用法示例：

  ```html
  <template>
    <div id="example">{{ message }}</div>
  </template>

  <script>
    const app = new Vue({
      el: "#example",
      data: {
        message: "Hello",
      },
    });
    method: {
      updateMessage() {
        this.message = "Hello World";
        console.log(this.$el.innerText); // Hello
        this.$nextTick(function () {
          console.log(this.$el.innerText); // Hello World
        });
      },
    },
  </script>
  ```
