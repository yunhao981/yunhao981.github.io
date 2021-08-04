---
title: test-day-1
show: true
date: 2021-08-04 00:37:09
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
---
每天总有一种事情做不完的感觉

今天刚来先配置了下One Box

VM设置好了，后面还需要提交一个merge request再进行下一步

和钟璐一起check了下运行的情况和版本号记录

摸了摸jenkins的pipeline迁移

把p4上的四个item，根据Configuration照葫芦画瓢在test-infra的Jenkins上分别创建了对应的item

Build failed两个

Audit_tools是因为测试用的git版本号并不存在对应的分支，

另一个component_audit是因为我事先并不知情某个目录名的设置需要更改

顺便就复习了下git和eci的分支命名规范

明天再和她确认下具体流程 尤其是release部分 Kyle说过要特别关注

还想看Fastrun的前端源码

下午和James Qian一起创建了Fastrun Daily，用于记录fastrun上一些随机的bug，目的是为了改善fastrun

需要关注非develop标注的运行错误，打开debug开关，根据报错的信息追踪Jenkins上的console log

如果是timeout就不用特别关注，permission denied应该也不必吧

如果是test failed也不用特别详细去看，记录下test即可

如果是maven build failure也不用，大概率是代码本身的问题

error要看最早的那个，并不一定会有“ERROR”字样的提示

先熟悉工作的流程

然后想办法搞个自动化

今晚想要继续更新自己的博客

到家的精力倒是比昨天好一些
