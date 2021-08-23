---
title: test-day-14
categories: test
tags: test
description: 服务器磁盘空间不足，beautify console log，fix onebox setup page bug
show: true
date: 2021-08-23 18:00:23
---

又是一个新的 cut，我的分工依旧不多，其实想多做一点事情的

在 keymaster build image 的时候，发现服务器磁盘空间不足，发了邮件去问了 24x7 解决

组会的时候听 Yubo Li 介绍了他上份工作的内容，觉得很厉害

如果是我的话不知道会怎么样处理

接到了新的两个支线任务，整理 component audit pipeline 的 console output，

如果是有包含 error 或者 exception 的字样，标成红色，然后给出一个用户友好的提示

大段大段的加载内容，直接放在 log 里，就不要打印在屏幕上了

fastrun build 的 Jenkins file 这一点做的相当友好，照猫画虎试试

另一个支线任务是修 Onebox setup page，单个页面的前端 bug

回家得恶补 react

