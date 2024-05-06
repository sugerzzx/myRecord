# What is StencilJS

[Overview](https://stenciljs.com/docs/introduction)

Stencil 是一个生成 Web Components（更具体地说是 Custom Elements）的**编译器**。 Stencil 将一些最流行框架的最佳概念结合到一个简单的构建时工具中。

Stencil 使用 **TypeScript、JSX** 和 CSS 创建符合标准的 Web 组件，可用于制作高质量的组件库。

使用 Stencil 生成的 Web Components 可以直接与流行的框架一起使用。 此外，Stencil 还可以生成特定于框架的包装器，允许 Stencil 组件与特定于框架的开发人员体验一起使用。

与直接使用 Custom Elements APIs 相比，Stencil 提供了更为方便的 API，使编写快速组件变得更加简单。 借助 **Virtual DOM**、**JSX** 和**异步渲染**，可以轻松创建快速且功能强大的组件，并且仍 100% 兼容 Web Components 标准。 除了使编写自定义元素变得更加容易之外，Stencil 还在 Web 组件之上添加了许多关键功能，例如**预渲染**和 _objects-as-properties_（而不仅仅是字符串）。

开发人员体验也进行了调整，并带有实时重新加载和编译器中内置的小型开发服务器。

## Web Component

[Web Component](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_components)

Web 组件是一种用于构建可重用、独立的 Web 界面元素的技术和规范，旨在提供一种跨框架、跨平台的组件化开发方式。Web 组件包括以下几个主要部分：

1. **自定义元素（Custom Elements）**：Web 组件的核心是自定义元素，它们是基于 Web 标准的扩展，使您可以定义自己的 HTML 元素。这些自定义元素具有自定义的标签名，例如`<my-component>`，并且可以包含自己的 HTML 内容、JavaScript 行为和样式。自定义元素采用类似于类的 JavaScript 对象来定义其行为。

2. **Shadow DOM**：Shadow DOM（影子 DOM）是一项技术，允许将组件的 DOM 结构封装在一个隔离的 DOM 树中，不受外部 CSS 和 JavaScript 的影响。这有助于避免样式冲突和组件封装。

3. **HTML 模板（HTML Templates）**：HTML 模板是定义自定义元素的标记内容的一种方式。使用模板，您可以将 HTML 结构封装在组件中，以便稍后动态生成和渲染。模板通常与 Shadow DOM 结合使用。

4. **HTML 导入（HTML Imports）**：HTML 导入是一种用于导入和重用 HTML 模块的机制。尽管 HTML 导入不是标准的 Web 组件规范的一部分，但它们可以用于将组件的 HTML、CSS 和 JavaScript 打包成独立的模块。

Web 组件的优点包括：

- **可重用性**：您可以创建自定义元素，并在应用程序中多次使用它们，提高代码的重用性。

- **封装性**：Shadow DOM 和封装的样式可以防止组件内部的样式和逻辑影响到应用程序的其他部分。

- **互操作性**：Web 组件可以与各种前端框架和技术一起使用，因为它们是基于 Web 标准的。

- **维护性**：Web 组件的独立性使其更容易维护和测试。

然而，Web 组件也面临一些挑战，包括浏览器兼容性问题和复杂的开发流程。为了更轻松地创建和使用 Web 组件，许多现代前端框架和库提供了对 Web 组件的支持和封装，使其更易于集成到应用程序中。

# Components

## Properties

[Props 是自定义的属性(attributes)/参数(parameters)，他们使开发者可以向组件中传递数据用于渲染(render)或者其他用途。](https://stenciljs.com/docs/properties)

### Prop 装饰器(@Prop())

在组件中使用 Stenci 装饰器`@Prop()`来声明 props

```ts
// First, we import Prop from '@stencil/core'
import { Component, Prop, h } from "@stencil/core";

@Component({
  tag: "todo-list",
})
export class TodoList {
  // Second, we decorate a class member with @Prop()
  @Prop() name: string;

  render() {
    // Within the component's class, its props are
    // accessed via `this`. This allows us to render
    // the value passed to `todo-list`
    return <div>To-Do List Name: {this.name}</div>;
  }
}
```

Stencil will expose name as an attribute on the element, which can be set wherever the component is used:

```jsx
/* Here we use the component in a TSX file */
<todo-list name={"Tuesday's To-Do List"}></todo-list>
```

```html
<!-- Here we use the component in an HTML file -->
<todo-list name="Tuesday's To-Do List"></todo-list>
```

### Variable Casing

[HTML 中的 attribute 名是大小写不敏感的，所以浏览器会把所有大写字符解释为小写字符。这意味着当你使用 DOM 中的模板时，camelCase (驼峰命名法) 的 prop 名需要使用其等价的 kebab-case (短横线分隔命名) 命名：](https://v2.cn.vuejs.org/v2/guide/components-props.html#Prop-%E7%9A%84%E5%A4%A7%E5%B0%8F%E5%86%99-camelCase-vs-kebab-case)

```html
<todo-list-item thing-to-do="Learn about Stencil Props"></todo-list-item>
```

# Testing

## Overview

为了确保组件按照预期方式工作和展示，Stencil 提供了开箱即用的工具以用来进行测试，包括单元测试和端到端测试。

### 单元测试对比端到端测试

在 Stencil 中：

**单元测试**侧重于单独测试*组件的 methods*。 例如，当一个方法被赋予参数 X 时，它应该返回 Y。

**端到端测试**重点关注**组件如何在 DOM 中呈现**以及各个**组件如何协同工作**。 例如，当 my-component 具有 X 属性时，子组件将渲染文本 Y，并期望接收事件 Z。

### 支持的工具

Stencil 目前支持以下工具来测试组件：

- **Stencil Test Runner**：一个 Stencil 自带的、基于 Jest 的用于 UT 和 e2e Testing 的测试工具，并且使用 Puppeteer 在实际浏览器中运行，以提供更真实的结果。

- **WebdriverIO**：Node.js 的浏览器和移动自动化测试框架，允许您跨所有浏览器运行组件和端到端测试。

- **Playwright**：一个自动化的端到端测试框架，可以在所有主要浏览器上运行

## Stencil Test Runner

### Overview

Stencil 有一个内置的测试运行程序，基于 Jest 和 Puppeteer

> Puppeteer 是一个基于 Node.js 的库，它提供了一个高级 API，用于通过开发者工具协议（DevTools Protocol）来控制 Chrome 或 Chromium 浏览器。它的主要功能是通过模拟用户行为来执行各种浏览器操作，比如加载页面、点击按钮、填写表单等。Puppeteer 默认以无界面模式（headless）运行，但也可以配置为以完整模式（headful）运行，即显示浏览器窗口。这使得 Puppeteer 成为一个强大的工具，可以用于自动化测试、网络爬虫、网页截图生成等各种用途。

#### 测试命令

模板测试使用命令 `stencil test` 运行，后跟一个或多个可选标志：

- `--spec`：运行单元测试

- `--e2e`：运行端到端测试

- `--watchAll`：监视所有测试文件的更改，并在更改时重新运行测试
  指定要运行的测试文件的路径。默认情况下，它将运行所有位于 `src/components/**/*.spec.ts` 中的测试文件。

下面是一系列示例 npm 脚本，可以将其添加到项目的 package.json 文件中以运行 Stencil 测试：

```json
{
  "scripts": {
    "test": "stencil test --spec",
    "test.watch": "stencil test --spec --watchAll",
    "test.end-to-end": "stencil test --e2e"
  }
}
```

##### 配置

Stencil 将应用它已经收集的数据的默认值。 例如，Stencil 已经知道要查看哪些目录，以及哪些文件是 spec 和 e2e 文件。 仍然可以使用相同的配置名称来配置 Jest，但现在使用模板配置测试属性。 请参阅测试配置文档以获取更多信息。

##### 命令行参数

虽然 Stencil CLI 提供了一组特定的命令行标志来指定，例如 要运行哪种类型的测试，您还可以通过 CLI 访问所有 Jest 选项。 例如，要指定单个测试，您可以通过添加 -- 向 Jest 传递位置参数，例如：

```bash
# run a single unit test
npx stencil test --spec -- src/components/my-component/my-component.spec.ts
# run a single e2e test
npx stencil test --e2e -- src/components/my-component/my-component.e2e.ts
```

除了位置参数之外，Stencil 还传递某些 Jest 特定标志，例如：

```bash
# enable code coverage
npx stencil test --spec --coverage
```
