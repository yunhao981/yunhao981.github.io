---
title: test-day-34
categories: test
tags: test
description:  昨日手撸前缀树，今朝开起马拉车
show: true
date: 2021-09-17 17:30:37
---

在刷 leetcode 的时候试着用了前缀树和 Manacher 算法

对自动补全代码提示的出现过程到底发生了什么，以及是怎么做到那么快的提示，有了一丢丢感性的概念

Manacher 可以用来找最长回文子串，而找最长回文子串的用途是啥我倒是也不清楚

利用了回文子串左右对称的性质，引入了臂长的概念，镜像对称地更新对应的两个位置

复杂度居然可以从平方降到线性

几乎是魔法一样的了