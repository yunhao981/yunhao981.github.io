---
title: test-day-22
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-09-02 00:31:35
---
今天的分支版本非常非常多，开会确认了具体的细节

下午几乎又扑在了 code merge pipeline 的 debug 上

测试了昨天写的合并 merge 与 recut

把 token 从本地文件换成了 Jenkins Credentials

一开始写的时候想的太复杂了，其实对于 Secret File，

```groovy
withCredentials([string(credentialsId: 'mytoken', variable: 'TOKEN')]) {
    echo "$TOKEN"
}

```
显然这个 TOKEN 是不会被 echo 出来的

每天水一发日记混 github commit 也真的是不太行

开日记的初衷是为了记录技术上的学习和成长来着

还是想要多写点 Night shift 时期的学习笔记

比如说今晚又和 react 擦出了怎么样的火花