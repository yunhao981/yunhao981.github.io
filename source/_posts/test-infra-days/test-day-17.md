---
title: test-day-17
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-08-25 18:29:28
---
早上发现上回的 cut 漏掉了 guardiola，是人工检查的时候出的差错

后来 James 开了个 pipeline 来让糊成一团的 console log 变得更友好

写了个框架，后面的我来填

其实就是不同的 component 信息，难受的点在于确认既没有多出来，也没有漏掉

大体找了一些，明天会继续做这件事情，对照 component list 和历史记录

今天也是一下午都在fix fast-liquibase pipeline

从 Infra Team 那里得到了回答，对包里没有 my-liquibase.py 的加入了对 cassandra.py 的支持

然后发现 liquibase 这个文件没有执行权限，所以脚本里也处理了下

在测 porpoise 的时候发现 jdbc_url 配置有问题，向 Zezhou Li 提了个 MR

和 James 和 Lu Zhong 开了个小会，我需要弄明白 sox-audit 和 component_audit 这两个的 Java 部分

Script 部分由 Lu Zhong 负责，而我也需要懂一些

其中有个文件里写了一些需要跳过的 components，后面需要确认这些是否依然需要跳过

和谁确认？明天再来问问 Kyle

明天还需要来重点着手解决 component audit pipeline 的 error log

上回的 java service 后来又变成了用 git 和 gitlab 的 api 来解决

好像是变成了用 pipeline 来做，还需要去玩一下如何把 csv 转成 markdown 的格式

