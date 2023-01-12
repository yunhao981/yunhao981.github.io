---
title: test-day-279
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2023-01-11 10:14:21
---
## Today's Task

- [ ] SlackBot Recut Flow
- [x] deploy stg job less timeout
- [x] skip wip pods on AWS
- [x] message channel to public
- [x] catlaog liquibase image trigger
- [x] keymaster liquibase conf path support
- [x] fix 'null' prefix in build description

## Additional Task

## Thought

### 1

Keymaster Liquibase Job 花了很久 debug

keymaster image -> docker image for liquibase k8s job -> run on k8s pods

entrypoint.sh 里面的改动需要重做 keymaster image 之后才会对 liquibase job image 生效

liquibase job image 用 km image 的 binary version 作为 tag

改完 script 之后再 build 的时候 tag 也是同一个。。。

相当于 image 里面的东西没有变

### 2

总感觉时间不够用
