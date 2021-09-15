---
title: test-day-32
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-09-15 18:17:50
---

昨晚起的 fastrun regression 全部失败了，

原因是 nucleus release branch 里的 code 本身就有 bug

而 regression 涉及到的那些 components 都依赖 nucleus 

后来和 Leo 一起找到了导致 CHG0150424—INT 出现 FakedFailCase 的 log

出现的原因是在对应标签组 build 的过程中 test case 数量为 0

需要去 fastrun 上挨个翻日志找到 case 0, failed 0, pass 0,

还会出现 BUILD FAILURE，尽管那个 fastrun job 可能是全部成功的小绿点

下午看了 JS 异步和 React Ref ，以及 TypeScript 相关的内容，写了点小笔记

但真正掌握还是需要回家写 Demo

开发进度相当慢