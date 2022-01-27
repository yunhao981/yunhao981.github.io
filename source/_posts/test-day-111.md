---
title: test-day-111
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-01-27 11:12:43
---
## Today's Task
- [ ] [ASAP] Property Page

## Additional Task 

## Thought

# 1

比较理想的时间表：

10:00 audit & merge

10:30 build image

11:45 deploy STG

12:00 start regression

16:00 regression report

冷冰冰的残酷现实：

现在每一步都有大概率出问题，耽误时间

互相又是层层递进的依赖关系

Audit 的过程中，有改动的 repo 结果会漏，而且跑一轮半小时，急需大改

build image 每隔三个月会遇到一次 token expire，偶尔服务器也会写满

deploy to STG 的时候经常容易起不来，另外目前 rating 不支持 aws，要暂时去掉

# 2

最近感兴趣的主题报菜名：

Cassandra, Zookeeper, ActiveMQ, Redis

Spring Boot, Kotlin, Ktor, Javalin 

Typescript, React, Vue

想要知道它们怎么用

还想知道更多关于 V8 的内容

以及曾经欠下来的各种力量小黑砖合集

来不及看的书，堆成小山那么高

# 3

Release Script migration

提一些通用 common methods 复用，节省工作量
