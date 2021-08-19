---
title: test-day-13
categories: test
tags: test
description: fast-liquibase pipeline进度终于动了一丢丢
show: true
date: 2021-08-19 21:59:26
---

做 liquibase 和 刷 liquibase 的 pipeline 并不是同一个

做的是在 release 里，只要确认参数和 image 对的上就好了

刷的是要修的，发现漏了 nexus 和 catalog

刚开分支准备动手，在 nucleus/test/build_job.sh 里有个涉及到 deploy liquibase 的部分

想往里面补上 nexus 和 catalog 的部分

结果发现三个月前上一个人把这两个从里面删掉了？？？

明天新的 cut ，todo 估计是赶不上了