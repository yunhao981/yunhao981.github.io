---
title: react-refs
categories: react
tags: react
description: 看起来很吓人的 refs
show: true
date: 2021-09-15 16:24:01
---

refs 可以用来访问 DOM 节点 或者 render() 里面创建的 react elements

父组件通常只能通过 props 和子组件交互，如果子组件需要修改，就要重新 render

# 使用条件

触发动画

管理焦点，选择文本，播放媒体

集成第三方 DOM 库

Avoid using refs for anything that can be done declaratively.

