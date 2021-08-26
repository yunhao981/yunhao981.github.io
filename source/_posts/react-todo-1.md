---
title: react-todo-1
categories: react
tags: react
description: 基本概念和函数组件
show: true
date: 2021-08-27 00:03:36
---
```
npx create-react-app moz-todo-react
```

直接上脚手架，虽然下载会花上许多时间，但还是可以有一个最最基础的目录结构

用 yarn 的话，带上 `--use-npm`

# 基本概念

源码在 src 里（废话

index.js 可以视作整体的入口，但更为核心的内容往往都在 App.js　里

脚手架帮忙做了相当多的事情，最核心的是　ReactDOM.render 那一段

```js
ReactDOM.render(
  <React.StrictMode>
    <App tasks={DATA}/>
  </React.StrictMode>,
  document.getElementById('root')
);
```

这里的 tasks 目前是传递给 App　这个 Component 的 Prop

和 HTML 属性很像，但在 JSX 里面 class 会叫做 className 来避免和 ES6　语法糖冲突

JSX 里只能用表达式, 语句NG

# Components

有用 class 的, 也有用 function 的

涉及到 state 的时候, 用 class 

今天先跟着教程写了 function 的那种

```js
export default function Todo(props) {
    return (
        // JSX stuff
        {props.xxx}
    );
}
```

大概这样就可以在里面用外面通过 props 传给 Component 的一些数据了

在需要传的数据有很多的时候这样一个个写出来会很吓人

