# 认识 KoaJS

## 什么是 KoaJS

KoaJS 是一个基于 NodeJS 的 Web 开发框架，它的特点是轻量、灵活、可扩展。KoaJS 的核心是中间件（Middleware），它提供了一种优雅的方法来编写 Web 服务器。

## KoaJS 的特点

- 轻量：KoaJS 的核心代码只有 550 行，它的代码量比 Express 少了很多，这也是它的一个优点，因为代码量少，所以它的维护成本也低，而且它的代码量少，所以它的学习成本也低。

- 灵活：KoaJS 的核心代码只提供了一些基础的功能，比如路由、请求、响应等，其他的功能都是通过中间件来实现的，所以它的灵活性很高，我们可以根据自己的需求来选择需要的中间件。

- 可扩展：KoaJS 的中间件机制使得它的可扩展性很高，我们可以根据自己的需求来编写中间件，也可以使用其他人编写好的中间件。

## KoaJS 的中间件机制

KoaJS 的中间件机制是它的核心，也是它的灵魂，所以我们必须要了解它的中间件机制。

### KoaJS 的中间件机制的实现原理

KoaJS 的中间件机制的实现原理是基于洋葱模型的，所谓的洋葱模型就是一个中间件的执行顺序是先进后出的，比如我们有一个中间件数组，它的顺序是 `A -> B -> C`，那么它的执行顺序就是 `C -> B -> A`,即按堆栈的方式组织和执行的。

### KoaJS 的中间件机制的实现代码

```ts
import Koa from "koa";
const app: Koa<Koa.DefaultState, Koa.DefaultContext> = new Koa(); // 创建 Koa 实例,类型为一个泛型

/* 注册中间件 */
app.use(async ctx:Koa.Context => { // Koa.Context 是 Koa的上下文对象
  ctx.body = "Hello World"; // 设置响应体
});

app.listen(3000);
```

上面的代码中，我们使用 `app.use` 方法注册了一个中间件，这个中间件的作用是设置响应体为 `Hello World`，我们可以看到 `app.use` 方法**接收一个函数作为参数，这个函数就是中间件**，它的参数是一个上下文对象，我们可以通过这个上下文对象来获取请求和响应的信息，比如请求体、响应体等。

这样，当我们访问 `http://localhost:3000` 时，就会返回 `Hello World`。

## 使用 KoaJS 开发 Web 服务器

### 安装 KoaJS

```shell
npm install koa @types/koa --save // ts
```

### 在 src/index.ts 中编写代码

```ts
// src/app/index.ts
import Koa from "koa";
const app: Koa<Koa.DefaultState, Koa.DefaultContext> = new Koa();

app.use(async ctx:Koa.Context => {
  ctx.body = "Hello World";
});

app.listen(3000);
```

### 添加路由

```bash
npm install koa-router @types/koa-router --save
```

```ts
// src/router/someRoute.ts
import Router from "koa-router";
import { Context } from "koa";

const router: Router<any, {}> = new Router({ prefix: "/user" }); // prefix: '/user'表示该路由下的所有路由都会加上前缀/user

router.get("/", async ctx:Context => {
  ctx.body = "Hello User";
});

export const userRoutes = router.routes();
```

```ts
// src/app/index.ts
// ...

const app: Koa<Koa.DefaultState, Koa.DefaultContext> = new Koa();

app.use(userRoutes); // 注册路由

app.listen(3000);
```

这样在我们访问 `http://localhost:3000` 时，就会返回 `Hello World`，访问 `http://localhost:3000/user` 时，就会返回 `Hello User`。

### koa-body 中间件

koa-body 中间件可以用来解析请求体，它支持解析 JSON、表单、文本等格式的请求体。

```shell
npm install koa-body --save
```

```ts
// src/app/index.ts
//...

const app: Koa<Koa.DefaultState, Koa.DefaultContext> = new Koa();

app.use(koaBody()); // 注册 koa-body 中间件
app.use(userRoutes);

/// ...
app.listen(3000);
```

同时，可以把 router.post()中的回调单独拆分到一个 controller 中，这样代码更加清晰。

```ts
// src/router/someController.ts
// ...
class UserController {
  async register(ctx: Context) {
    ctx.body = "register";
  }
  async login(ctx: Context) {
    console.log(ctx.request.body); // 通过koa-body中间件获取请求体
    ctx.body = JSON.stringify(ctx.request.body);
  }
}
export const { register, login } = new UserController(); // 导出实例化后的对象
```
