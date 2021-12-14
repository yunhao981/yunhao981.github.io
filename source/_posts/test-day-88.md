---
title: test-day-88
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-12-14 10:32:43
---
## Today's Task
- [ ] Split CheckSTG
- [ ] Transfer Jenkins Jobs
- [ ] Add a page to search properties on ReleaseMe
    - [ ] Router without React Router
- [ ] Onebox-setup Dockerfile Debug
- [ ] Add comment time to ReleaseMe

## Additional Task 
- [x] Rebuild ALL LB Team Components Images for INT
- [x] Rebuild them for PROD
- [x] Long term tasks list

## Thought

### 1

昨晚运动量太大了…

不仅晚上睡不着

早上还全身酸痛

今天就骑台子吧…

### 2

需要一份中短期的 target list

短期两周的我觉得我可以直接用每天的 task list

长期的目标我其实有点懵

不过列计划然后执行这种事情

无论我 fail 多少次

定计划的时候都还是很爽

### 3

后来忙了一下午 log4j 的事情

其实并不需要我来修

只是帮忙重新 build 所有涉及到的 40 多个 image

fast-liquibase 的流程变动

涉及到了 ESS Secret

就需要手动上 STG 进去执行脚本

Tommy Tao 写的，暂时还只支持 nucleus

好消息是 Cassandra 和 Liquibase 都支持

后面会慢慢切换到他的那些
