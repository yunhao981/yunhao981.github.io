---
title: test-day-63
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-11-09 18:29:55
---
很久之前忘记了问 DBA review Keymaster liquibase

今天的 cut 碰到了诸多问题

idgen 的 aws registry 没有对应的 pod

saola 全家桶直接 compilation failure

code redemption 和 venice STG 起不来

代码原因？可能是镜像没有 push 到 CIAWS 上

用旧机器搭了个 Linux，装好才发现其实用起来和虚拟机没什么区别

Jenkins job 迁移进度推进了一丢丢，成功地跑了 build sloth

还有 INTBVT 也得到了预期的结果