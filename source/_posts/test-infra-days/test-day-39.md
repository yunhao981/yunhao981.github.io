---
title: test-day-39
categories: test
tags: test
description: 手上的 task 又推进了一丢丢
show: true
date: 2021-09-29 17:15:30
---
思索了好久 checkbox + radioGroup 的组合逻辑

最终把它们拆分开来，checkbox 和 radiogroup 各自拥有独立的事件处理

然后这两个指向统一的一个函数，用来拼凑出这个组件本身的命令，

最终把这个命令通过 this.props.onChange 回调函数传给它的父组件

然而不同组件间命令的组合，远远不仅仅是直接把它们一个个加起来那么简单

cut build 碰到了小麻烦

nexus image build 不通过

最后下午查出来是配置文件的版本号写错了

从 551.0.1 被改成了 1000.0.0

也不知道这么做的目的是什么…

要好好 push 一下自己的进度