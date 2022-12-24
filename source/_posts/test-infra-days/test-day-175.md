---
title: test-day-175
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-08-01 10:21:46
---
## Today's Task
- [ ] Build Script User Friendly Changes
    - [x] Extract Common Methods for PCT jobs
    - [x] Remove Audit Tool from old repo
- [ ] Hadar Groovy Liquibase Job Support

## Additional Task 
- [x] Fix ReleaseProductInNucleus pipeline (Token Expired)

## Thought

又是新的一个月

这个月可以拿满 leetcode 每日一题徽章吗

Jenkins declarative pipeline script 可以通过这样的办法去复用方法

```groovy
stage('init') {
    agent any
    steps {
        script {
            utils = load 'PCT/common_utils.groovy'
        }
    }
}
```

复用出去以后虽然可以让代码结构更加干净，未来有改动的话也可以省力一些

但是没有一个好用的编辑器插件支持，跳转到方法定义的体验相当差劲
