# JS

## Js 是解释型语言还是编译型语言？

答：[JavaScript is generally considered an interpreted language, but modern JavaScript engines no longer just interpret JavaScript, they compile it.](https://nodejs.org/en/learn/getting-started/the-v8-javascript-engine#compilation)

这句话指的是 JavaScript 通常被认为是一种解释型语言，但是现代 JavaScript 引擎已经不仅仅是解释 JavaScript 代码了，它们对其进行了编译。让我们来拆解一下：

1. **解释型语言（Interpreted Language）**：这种语言的代码在运行时逐行被解释器执行，不需要事先编译成机器码。JavaScript 通常被归类为解释型语言，因为它在运行时由浏览器或 Node.js 解释器逐行执行。

2. **编译（Compilation）**：编译是将高级语言代码（如 JavaScript）转换为低级代码（如机器码）的过程。传统上，编译器会在代码执行之前将代码转换为机器码，这样执行时速度更快。编译通常被认为比解释更快，因为编译后的代码直接在计算机上运行，而不需要解释器逐行解释。

3. **现代 JavaScript 引擎（Modern JavaScript Engines）**：主要指浏览器内置的 JavaScript 引擎（如 Chrome 的 V8 引擎、Firefox 的 SpiderMonkey 引擎等）以及 Node.js 中使用的引擎（也通常是 V8）。这些引擎经过了多年的优化和发展，已经不再仅仅解释 JavaScript 代码，而是将其编译成更高效的形式。

### js 如何被编译

1. **即时编译（Just-In-Time Compilation，JIT）**：现代 JavaScript 引擎通常采用 JIT 编译技术。JIT 编译器在运行时分析代码，并将其部分或全部编译成本地机器码，以便更快地执行。这使得 JavaScript 代码的执行速度接近于原生的编译语言。

2. **优化技术**：JavaScript 引擎使用各种优化技术来提高代码执行效率，例如内联缓存、逃逸分析、循环优化等。这些技术可以使得 JavaScript 代码在运行时更快地执行，并且更有效地利用计算资源。

3. **多层次编译**：JavaScript 引擎通常采用多层次的编译策略，将 JavaScript 代码从高级别的抽象语法树（AST）逐步转换为低级别的机器码。这种分阶段的编译过程可以更好地适应代码的特征，并生成更优化的机器码。

4. **内存管理优化**：现代 JavaScript 引擎还会对内存管理进行优化，例如使用垃圾回收算法来自动释放不再使用的内存，以减少内存占用和提高性能。

综上所述，将 JavaScript 代码编译成更高效的形式意味着通过优化和转换，使得代码在执行时更快速、更高效，并且能够更好地利用计算资源。这些优化使得 JavaScript 代码在现代浏览器和 Node.js 环境中能够达到接近原生代码的性能水平。

## js 异步编程

### 什么是 nodejs(js) 事件循环

[The event loop is what allows Node.js to perform non-blocking I/O operations — despite the fact that JavaScript is single-threaded — by offloading operations to the system kernel whenever possible.](https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick#the-nodejs-event-loop)

这句话解释了 Node.js 中事件循环（event loop）的作用以及 JavaScript 单线程特性下如何实现非阻塞 I/O 操作的原理。让我们逐步解释：

1. **事件循环（event loop）**：事件循环是 Node.js 的核心机制之一，用于处理异步操作和事件驱动的编程范式。它负责接收和分发事件，并且在事件发生时执行相应的回调函数。

2. **JavaScript 的单线程特性**：JavaScript 是一种单线程语言，意味着它只有一个主线程来执行代码。在传统的同步编程模型中，当主线程执行 I/O 操作时会发生阻塞，直到操作完成才能继续执行后续代码。

3. **非阻塞 I/O 操作**：为了避免主线程的阻塞，Node.js 采用了非阻塞 I/O 操作。这意味着当主线程发起一个 I/O 操作（如文件读取、网络请求等）时，它不会等待操作完成，而是立即继续执行后续代码。

4. **操作系统内核的利用**：Node.js 通过将 I/O 操作委托给操作系统内核来实现非阻塞 I/O。操作系统内核负责管理系统资源，并且通常会提供一些**异步操作的 API**，允许程序发起 I/O 请求而无需等待操作完成。这样，当 Node.js 发起一个非阻塞 I/O 操作时，操作系统内核会在后台处理这个操作，同时允许 Node.js 主线程继续执行其他代码。

**综上所述**，事件循环是 Node.js 实现非阻塞 I/O 操作的关键机制之一。它允许 Node.js 主线程在执行 I/O 操作时不被阻塞，通过将操作委托给操作系统内核并利用操作系统提供的异步 API 来实现。这使得 Node.js 能够高效地处理大量并发的 I/O 操作，从而提高了应用程序的性能和吞吐量。

上述特性同样适用于浏览器中的 JavaScript。虽然浏览器和 Node.js 是不同的环境，但它们都采用了类似的事件驱动和异步编程模型，以处理 I/O 操作和其他异步任务。

在浏览器中，JavaScript 同样是单线程的，主要负责处理用户界面和执行 JavaScript 代码。然而，浏览器环境与 Node.js 不同，它还必须处理用户交互、渲染页面和网络请求等任务。

**因此**，浏览器中的 JavaScript 同样利用事件循环和非阻塞 I/O 操作来处理异步任务。例如，浏览器中的 Ajax 请求、DOM 事件处理、定时器等都是异步的，它们不会阻塞主线程的执行，而是通过事件循环和回调函数来处理。

#### Event Loop 解释

让我们一步一步来理解 Node.js 启动过程及其事件循环如何工作：

1. **初始化:** 当您启动 Node.js 应用程序时，它首先会初始化一些内部变量和设置，例如全局对象和模块系统。

2. **处理输入脚本:** 接下来，Node.js 会处理您提供的脚本文件。该脚本可能会包含同步和异步代码。

   - **同步代码:** 同步代码会一行一行地执行，直到完成。在此期间，事件循环会阻塞，不会处理任何其他任务。

   - **异步代码:** 异步代码不会阻塞事件循环。相反，它会将任务委托给其他线程 (例如，操作系统线程) 来处理，然后继续执行后续代码。当异步操作完成时，它会将结果放入事件队列中，通知事件循环进行处理。

3. **事件循环:** 处理完输入脚本后，Node.js 就进入了主循环，即事件循环。事件循环是一个不断运行的程序，它会一直执行以下操作，直到进程退出：

   - **检查事件队列:** 事件队列是一个存储待处理任务的列表。这些任务可能是来自完成的异步操作的回调函数，也可能是使用 `setTimeout` 或 `setInterval`之类的函数 schedulers 的计时器回调函数。

   - **处理队列中的任务:** 事件循环会依次处理队列中的任务，遵循先进先出 (FIFO) 的原则。对于每个任务，它都会调用相应的回调函数来执行相应的操作。

   - **非阻塞 I/O:** 当遇到需要等待外部操作 (例如，网络请求或文件读写) 的 I/O 操作时，Node.js 不会阻塞事件循环。相反，它会将该操作委托给操作系统，然后继续处理其他任务。一旦操作完成，操作系统会通知 Node.js，然后事件循环会将相应的回调函数放入事件队列中以供稍后处理。

   - **空闲阶段:** 如果事件队列为空，并且没有其他待处理的任务，事件循环会进入空闲阶段。在空闲阶段，事件循环会等待 I/O 事件或计时器超时事件的通知。

```
一个简化的事件循环操作顺序流程图
   ┌───────────────────────────┐
┌─>│           timers          │
│  └─────────────┬─────────────┘
│  ┌─────────────┴─────────────┐
│  │     pending callbacks     │
│  └─────────────┬─────────────┘
│  ┌─────────────┴─────────────┐
│  │       idle, prepare       │
│  └─────────────┬─────────────┘      ┌───────────────┐
│  ┌─────────────┴─────────────┐      │   incoming:   │
│  │           poll            │<─────┤  connections, │
│  └─────────────┬─────────────┘      │   data, etc.  │
│  ┌─────────────┴─────────────┐      └───────────────┘
│  │           check           │
│  └─────────────┬─────────────┘
│  ┌─────────────┴─────────────┐
└──┤      close callbacks      │
   └───────────────────────────┘
```

> 每个方块都被称为事件循环中的一个“**阶段**”

每个**阶段**都有一个遵循先进先出 (FIFO) 原则的**回调队列**。事件循环依次处理这些阶段，每个阶段都会先执行该阶段特有的操作，然后依次处理队列中的回调函数，直到队列为空或达到最大回调处理限制。一旦处理完该阶段的队列，事件循环就会进入下一个阶段，继续按照同样的方式执行。

#### 阶段概述

1. **timers（定时器）**：

   - 在这个阶段，执行由 `setTimeout()` 和 `setInterval()` 安排的回调函数。

2. **pending callbacks（挂起回调）**：

   - 在上一个循环迭代中被延迟到下一个循环迭代的 I/O 回调函数被执行。

3. **idle、prepare**：

   - 这两个阶段通常只在内部使用，不对用户代码可见。

4. **poll（轮询）**：

   - 在这个阶段，Node.js 会检索新的 I/O 事件。大多数 I/O 相关的回调函数（除了被定时器安排的、以及 `setImmediate()` 安排的）都会在这个阶段执行。
   - 当没有任何计划的定时器和 `setImmediate()` 回调时，Node.js 将在这里阻塞，等待事件的到来。

5. **check（检查）**：

   - `setImmediate()` 回调函数在这个阶段被调用。

6. **close callbacks（关闭回调）**：
   - 一些关闭事件的回调函数在这个阶段被执行，例如 `socket.on('close', ...)`。

### 阶段详述

#### timers（定时器）

#### pending callbacks（挂起回调）

#### idle、prepare

#### poll（轮询）

#### check（检查）

#### close callbacks（关闭回调）

#### setImmediate 和 setTimeout

### process.nextTick

1. **`process.nextTick()` 不是事件循环的一部分**：

   - 尽管 `process.nextTick()` 是异步 API 的一部分，但它并不是严格意义上事件循环的一部分。它是在事件循环的特定阶段之后执行的。

2. **`process.nextTick()` 的执行时机**：

   - 当调用 `process.nextTick()` 时，它的回调函数会在当前**操作**（transition）完成后立即执行，而不受事件循环当前阶段的影响。这个**操作**通常是从底层的 C/C++ 处理程序转换为执行所需的 JavaScript。

3. **`process.nextTick()` 的影响**：
   - 在给定的事件循环阶段中调用 `process.nextTick()` 时，所有传递给 `process.nextTick()` 的回调都会在事件循环继续之前解析。这可能会导致一些问题，因为它允许您通过递归调用 `process.nextTick()` 来“饿死”您的 I/O，这会阻止事件循环进入轮询阶段。

这段话的重点在于强调 `process.nextTick()` 的特殊性，以及它对事件循环执行流程的影响。通过理解这些概念，可以更好地优化和管理异步代码，避免可能导致性能问题的陷阱。

### js 异步 api

在 Node.js 中，异步 API 通常涉及系统内核完成底层任务，比如文件 I/O 操作、网络通信等。Node.js 的 libuv 库会负责管理事件循环和异步操作，以确保高效执行。

> libuv 是一个跨平台的异步 I/O 库，由 C 语言编写，它为事件驱动的编程提供了一个统一的 API。它最初是为 Node.js 而开发的，但现在已经成为了一个独立的项目，并被许多其他软件项目采用。

而在浏览器中，JavaScript 的异步操作通常由浏览器自身的功能和 Web API 支持，比如 XMLHttpRequest、Fetch API 等。这些 API 提供了浏览器环境下执行异步任务的方法，并且浏览器会利用自己的网络堆栈来处理这些操作，而不是直接依赖系统内核。

### Promise

为什么需要 Promise，因为使用回调函数实现的异步编程，在连续执行两个或者多个异步操作时，会出现回调地狱的问题，代码难以维护和阅读。Promise 是一种更优雅的解决方案，它可以更好地处理异步操作，避免回调地狱的问题。

```js
// 使用回调函数实现异步操作
function readFile
('file.txt', function (err, data) {
  if (err) {
    console.error('Error reading file:', err);
  } else {
    console.log('File content:', data);
  }
});

// 使用 Promise 实现异步操作
const readFile = (filename) => {
  return new Promise((resolve, reject) => {
    fs.readFile(filename, (
      err,
      data
    ) => {
      if (err) {
        reject(err);
      } else {
        resolve(data);
      }
    });
  });
};

readFile('file.txt')
  .then((data) => {
    console.log('File content:', data);
  })
  .catch((err) => {
    console.error('Error reading file:', err);
  });
```

### queueMicrotask 和 prosess.nextTick

`queueMicrotask` 和 `process.nextTick` 都是用于在事件循环中插入微任务（microtask）的方法，它们的作用是在当前事件循环的末尾执行指定的回调函数。

[queueMicrotask 介绍](https://developer.mozilla.org/zh-CN/docs/Web/API/queueMicrotask)
[Microtask_guide 使用](https://developer.mozilla.org/zh-CN/docs/Web/API/HTML_DOM_API/Microtask_guide)

[Node 中的 queuemicrotaskcallback](https://nodejs.org/docs/v20.12.1/api/globals.html#queuemicrotaskcallback)
[Node 中的 processnexttickcallback-args](https://nodejs.org/docs/v20.12.1/api/process.html#processnexttickcallback-args)

#### queueMicrotask 和 prosess.nextTick 的执行顺序

在 Node.js 中，`process.nextTick` 的优先级高于 `queueMicrotask`，即 `process.nextTick` 的回调函数会在 `queueMicrotask` 的回调函数之前执行。

[Within Node.js, every time the "next tick queue" is drained, the microtask queue is drained immediately after.](https://nodejs.org/docs/latest/api/process.html#when-to-use-queuemicrotask-vs-processnexttick)

```js
// test.js
const { nextTick } = require("node:process");

Promise.resolve().then(() => console.log(2));
queueMicrotask(() => console.log(3));
nextTick(() => console.log(1));
// Output:
// 1
// 2
// 3
```

但是在 esModule 中,情况会有所不同

```js
// test.mjs
Promise.resolve().then(() => console.log(2));
queueMicrotask(() => console.log(3));
process.nextTick(() => console.log(1));
// Output:
// 2
// 3
// 1
```

[stackoverflow 上也有相关提问](https://stackoverflow.com/questions/70518968/process-nexttick-vs-queuemicrotask-in-commonjs-and-esm-what-is-the-execution-or)

解答：

在 Node.js 中，有几个不同的阶段组成了事件循环。其中，主要包括轮询（poll）、检查（check）、关闭（close）等阶段。在轮询阶段中，会处理 I/O 事件，执行定时器等待时间已到的回调，以及执行 `setImmediate()` 添加的任务。而在检查阶段中，会执行 `setImmediate()` 添加的任务。

在上述示例中，当脚本以 ES 模块（ESM）形式运行时，脚本实际上是在微任务阶段执行的，这是因为 ES 模块的执行被放置在一个微任务中。因此，通过 `queueMicrotask()` 添加的微任务会在当前微任务队列中执行，而此时还没有进行下一个事件循环阶段（例如检查阶段）。因此，无论是否还有 `process.nextTick()` 的回调，这些微任务都会优先执行。

然而，当脚本以 CommonJS 形式运行时，脚本的执行是在轮询阶段进行的。在这种情况下，`process.nextTick()` 的回调会在当前轮询阶段执行完毕后立即执行，而微任务则会在下一个事件循环的微任务阶段执行。因此，无论 `queueMicrotask()` 是否有回调，`process.nextTick()` 的回调都会先执行。

这就解释了为什么在上述示例中，以不同的模块加载方式运行时，输出结果会有所不同。

## JS 模块