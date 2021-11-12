---
title: test-day-66
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-11-12 17:14:25
---
cut build 还算是比较顺利

上 STG 手动刷了下 liquibase，

修改了 component audit v4 的输出格式

下次 cm 应该就可以用起来了

ReleaseMe 的 feature 改代码只花了 20 分钟

但为了让它跑起来，花了一整周的时间去搭环境

新的 linux 物理机，全新的 docker

以及用 idea 配置一个 spring boot 项目的 run configuration

插测试flow，用 postman 朝 backend webhook api 发一个 post

给 idea 换了个 terminal

```
C:\cygwin64\bin\bash.exe -ilc "cd ${OLDPWD-.}; bash"
```

powershell 我还是不喜欢