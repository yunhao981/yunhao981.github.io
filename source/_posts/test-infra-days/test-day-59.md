---
title: test-day-59
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-11-03 14:49:53
---
迁移 Jenkins Job 的问题一个个在找

需要注意的细节有很多

比如先前那个改 host 的，我一直是在 `master` 上看的，实际上这个 job 是在 `slave` 上运行的

所以 host 会不一样，要在 `configuration` 里面指定 job 在 master 上运行

同样的问题也导致了 Master_Lockbox_BVT 找不到 maven plugin

还碰到了git fetch 日常超时，这回找到了设置

 `Source Code Management` -> `Additional Behaviours` -> `Advanced clone behaviours`

 可以设置 Timeout 的分钟数

今天同时有新 CM 的 cut build， 迁移 job 的 debug， 修改 24 个 build.sh 里面的 AWS

在等待 git clone 的过程中，倒是可以异步去执行三件事情

ChromeDriver 的版本要和 Chrome 相匹配

对于这两个 Jenkins job，用 77 或者 93 要比 96 稳妥一些

可以用 -D 来指定 Properties