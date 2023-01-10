---
title: js-note-async
categories: JavaScript
tags: JavaScript
description: js 异步
show: true
date: 2021-09-15 14:49:03
---
# General Concepts

通常来说一个程序同时只做一件事情，

如果一个函数依赖另一个函数的运行结果，

就需要等待这个函数运行完毕后才能继续执行，

从用户的角度而言，程序是卡住的

# Blocking

Web App 在浏览器里执行一大段代码，并且没有交还控制给浏览器

# Threads

一个线程一次做一个task，tasks 序列执行

如果有多个线程，可以并行执行

通常，JS是单线程的

所以需要 web worker，可以把一部分进程塞给另一个线程

但它并不能和 DOM 交互，没法更新 UI

```
Main Thread: Task A --> Task B
```

如果 B 依赖 A 的结果，同时执行的话会有 error，因为 B 并没有得到结果就开始执行了

```
  Main thread: Task A --> Task B --> |Task D|
Worker thread: Task C -----------> |      |
```

如果 D 同时需要 B 和 C 的结果，如果 D 在缺少其中任何一个结果的情况下执行了，也会有 error

所以就需要有 Promise 之类的 Feature，可以在 A　和　B　之间再去做一些别的事情

# Async callbacks

把函数当参数传进去，它会在后台执行

执行完了之后会调用 callback 通知事情做完了

有点过时了

传进去的是引用，包在外面的那个函数负责执行

并不是所有的 callback 都是异步的

# Promises

promise 本身是个对象，表示异步操作的成功与否，是一个中间状态

大概就像是浏览器在说，“我保证会尽快给一个结果”

每个 `.then()` 都会返回一个promise，所以可以一路连下去

`.catch()` 可以抓到then()链里面的出现的任何错误

普通的 try catch 不能用，但可以配合 async await 使用

# Event Queue

异步操作会被放进事件队列，在主线程结束之后运行

