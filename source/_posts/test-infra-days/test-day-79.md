---
title: test-day-79
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-12-01 10:18:05
---
## Today's Task
- [ ] Add a page to search properties on ReleaseMe
- [ ] Add comment time to ReleaseMe
- [x] Rewrite Delete comment button API
- [ ] Transfer Jenkins Jobs
    - [x] Run LB_QAv5_INTBVT
    - [x] Run RL_CP_INT_PreProduction_INTBVT
    - [ ] Run Master_Lockbox_BVT

## Additional Task 
- [x] Rebuild ibex image
    - [x] Ask Jen to create repositories
    - [x] Fix ibex.grpc container script
- [x] Rebuild saola.infra image
    - [x] Ask Jen to create repositories

# Code Review

如果异步函数没有返回值，不用特地去 try-catch return null 啥的

如果要触发 react 页面的重新渲染，用 `forceUpdate()`，而不是 `setState({})`

后端自己本身也要判断

要按照参数的合法性去检查

后端的 api 不够 RESTful

请求一个长得很像的 api， `/comment/26` 这样子

然后根据给它不同的 Request Method 来执行不同的操作

怎么样把 api 写得更为 RESTful 呢？

## Thought

已经不知道多少次

梦见自己回到初中

这一回，是在熟悉的第一排

用湿巾纸反复擦拭桌面的油腻

不知道反映了什么心理活动

让弗洛伊德老爷子和周公一起同语文老师探讨探讨吧

我居然在中午

又一次闻到了

家乐福面包房的烘焙麦香

## 踩到的坑

saola.infra 的 image name 叫 `healthy-play` 而不是 `health-play`

中间差了一个 `Y`