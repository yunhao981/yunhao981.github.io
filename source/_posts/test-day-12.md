---
title: test-day-12
categories: test
tags: test
description: 写了solr.exporter pipeline；人工流程忘了merge，考虑写个todo list
show: true
date: 2021-08-18 16:46:50
---
今天一来就发现了 nexus 需要 recut，而且test case 败了非常多

最后查明原因是没有 merge 就 build image 了

我理解错了`nexus合进551，可以直接release build`的意思，认为已经全部merge完毕了

其实只是一个特定的 MR 合并进去了，并没有包含新的 CHG0150419 中所有的改动

下回在 build 之前，一定要确保已经merge了

今天重新进行了参数和状态的检查，nexus 和 nucleus 甚至需要 3rd recut

用fastrun 跑 regression 的时候，可以酌情考虑用 2 - 4 台 Docker Container 来跑，这样可以尽量避免出现因为机器本身原因而导致整体 fail 的状况

今天完成了 Nucleus.solr.exporter 的 build pipeline， 直接在 solr 的 build.groovy 里添加了一部分，照猫画虎，倒也能跑

一个值得注意的细节是，在一段 if-else 里面，如果出现重复定义同名变量的话，只会保留先定义的那个变量值。也就是说，尽量换个名字吧

想了想，还是得先搞个 todo list，试试 react 和 node 吧

纯靠短期记忆哪些 Component 的话，太容易出错了

之前的 fast-liquibase issue 还是没有头绪，到处都找不到涉及 Artifactory 的部分，说是在 mvn deploy 的时候会在那里创建对应版本号的文件夹

不知道应该如何解决