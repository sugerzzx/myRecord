# React

## TypeScript 类型

### `ComponentPropsWithoutRef<'div'>` 和 `React.HTMLAttributes<HTMLDivElement>`

`ComponentPropsWithoutRef<'div'>` 和 React.HTMLAttributes<HTMLDivElement> 这两个类型都代表了 React DIV 组件可以接受的属性类型,但有以下几点主要区别:

1. `ComponentPropsWithoutRef<'div'>` 包含了除了 ref 之外的所有内置属性,如 key、`children` 等。而 `React.HTMLAttributes<HTMLDivElement>` 只包含 HTML DIV 元素的属性。
2. `ComponentPropsWithoutRef<'div'>` 包含了 className 属性,对应到 DOM 的 class。而 `React.HTMLAttributes<HTMLDivElement>` 包含 class 而不是 className。
3. `ComponentPropsWithoutRef<'div'>` 包含了 React 组件特有的属性,如 onClick、`onChange` 等事件属性。`React.HTMLAttributes<HTMLDivElement>` 不包含这些 React 特有属性。
4. `ComponentPropsWithoutRef<'div'>` 会包含 div 组件定义的额外属性。`React.HTMLAttributes<HTMLDivElement>` 只包含原生 DIV 元素的属性。
5. `ComponentPropsWithoutRef<'div'>` 类型定义来自 react 包。``React.HTMLAttributes<HTMLDivElement>` 来自 @types/react`。
综上,`ComponentPropsWithoutRef<'div'>`比`React.HTMLAttributes<HTMLDivElement>` 更全面地表示一个 React DIV 组件的属性,所以在需要准确描述组件 props 时更推荐使用它。
