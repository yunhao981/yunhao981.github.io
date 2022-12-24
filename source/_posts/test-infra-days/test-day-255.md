---
title: test-day-255
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-12-01 15:36:50
---
## Today's Task

- [x] Fix Image jobs' message channel
- [x] Fix Image jobs' common baseimage
- [x] Fix Image jobs' tag check
- [ ] Start Hadar Flow on CM Day

## Additional Task 

## Thought

### 1

想再进一步减少常规 cm 流程的 manual step

在 cm cut 当天的上午 10:30 触发 audit

在 audit job 结束之后拿到准确的 component list

根据 component list 自动触发 code merge

用 jenkins 去起一个定时 job call hadar api，然后 hadar 再去起对应的 jenkins job

为什么不直接用 hadar...

### 2

hadar 的 groovy script exception 是放在 modal 里展示的 = =

这样其实根本来不及看，需要放到本地的某个文件里

### 3

hadar fetch job log

### 4 

Nav Bar simplification

CM 太多的时候不方便找

加个搜索框也好

### 5

如果 toliman 的 acl 搞不定的话

hadar start job 的时候没地方选需要用哪台 Jenkins

另外两台 jenkins 的 job 名称之间需要弄个 map

### 6

用 hadar 起 fastrun regression

### 7

Hadar Serialization (Restore status and progress after service restart)

### 8

Hadar Dark Mode

### 9 

Slack bot token 明文写在 code 里，修
