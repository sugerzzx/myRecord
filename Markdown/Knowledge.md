# HTML

# CSS

# JS

# WX

# VUE

### VUE2

###### 响应式原理

- ###### MVVM 模式

  MVVM 是 Model-View-ViewModel 的缩写,是一种软件架构模式。它是后端 MVC 架构模式的衍生模式,主要应用于前端开发。

  > Model:模型层,数据
  > View:视图层,UI
  > ViewModel:连接视图和数据的中间件,做数据绑定,实现了 View 和 Model 的解耦
  >
  > > 解耦是软件工程中的一个重要概念,是指使系统中的各个模块或组件之间的依赖关系最小化,独立性最大化,便于模块的重构和维护的一种设计思想。

- ###### Onject.defineProperty()方法

  `Object.defineProperty()`方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性，并返回此对象。并且可以定义特定属性，如

  ```js
  Object.defineProperties(obj, 'a' {
    value: 37, // 定义了obj对象的a属性值为37
    writable: true // 定义了obj对象的a属性为可写
    enumerable: true // 定义了obj对象的a属性为可枚举
    configurable: true // 定义了obj对象的a属性为可配置
  })
  ```

  > 并且，Object.defineProperty()方法定义的属性，不可修改，不可枚举，不可配置(不可删除).

  get 和 set 方法,在访问属性时会触发 get 方法,在设置属性时会触发 set 方法

  ```js
  let obj = {};
  Object.defineProperty(obj, "a", {
    get() {
      console.log("get");
    },
    set(val) {
      console.log("set");
    },
  });
  console.log(obj.a); // get undefined，因为get方法没有返回值，所以是undefined
  obj.a = 1; // set
  ```

  > 注意：get 和 set 方法与 value 和 writable 不能同时存在，否则会报错，因为 get 和 set 方法本质上就是是用来代替 value 和 writable 的。

- ###### Object.defineProperty()方法实现页面更新以及响应式原理

  ```vue
  <div id="app">{{a}}</div>
  // 触发了obj.a的get方法

  <script>
  let obj = {};
  let temp = "";
  Object.defineProperty(obj, "a", {
    get() {
      console.log("get");
      return temp;
    },
    set(val) {
      // val来自于obj.a = 1的1
      console.log("set");
      temp = val;
      document.getElementById("app").innerHTML = val;
    },
  });
  obj.a = 1; // set
  console.log(obj.a); // get 1
  </script>
  ```

  > 通过上面的代码，我们可以看到，当页面加载时，会触发 obj.a 的 get 方法，然后将 temp 的值赋给 div 的 innerHTML，当我们给 obj.a 赋值时，会触发 set 方法，然后将值赋给 temp，然后将 temp 的值赋给 div 的 innerHTML，这样就实现了页面的更新。
