---
title: test-day-444
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2023-09-05 15:50:52
---
## Today's Task

- [x] Fix git issue on china build host
- [ ] ReleaseMe Metrics FE
- [ ] ReleaseMe Metrics BE API

## Additional Task

- [x] Fix Regression Bot Parameters
- [x] Fix MR Bot fetching mr_id

## Thought

### 1

React 18 默认全是 hooks

useEffect() 里面如果更新了 state，而这个 state 会触发页面重新渲染的话，会死循环

### 2

IDEA 在处理 import generated sources 的时候容易找不到 generated classes

project right click -> maven -> generate sources and update folders

一般可以解决, 不行的话 mvn idea:module

### 3

不要在 controller 里去调另外一个 controller 的 method，这不清蒸

controller 里不要写太多逻辑
