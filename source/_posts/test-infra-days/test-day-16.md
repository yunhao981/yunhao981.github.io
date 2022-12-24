---
title: test-day-16
categories: test
tags: test
description: 接到了新的任务！fast-liquibase 推进一大步
show: true
date: 2021-08-24 18:39:11
---

今天花了很多时间在 fix fast-liquibase pipeline 上

问了很多问题，最后涉及到 Cassandra 的部分还是需要去问 Infra Team，等明天的答复

对照 wiki 确认了有 liquibase.data 的 component，接着再去 Artifactory 上一个个找到对应的 tarfile 文件夹路径，写了一长串极其吓人的 if-else，终于是能够成功获取到 tarfile 了

剩下的细节明天再来处理看看

也许大概从 Yanqin 那里接到了一个新的任务。

release步骤相当零散，做出来的 image 也是手工去填进 confluence，这个位置也没法填写进 pipeline

所以需要有一个中心化的 service，去存储每次 build 出来的 image 

两种实现方案，一种是调用 git 和 gitlab 的 api，更新文件从而生成一个 markdown

另一种是自己写一套，可以参考 ReleaseMe，照猫画虎搞个量产型

可以用 activemq 和 MySQL， 本地可以搭一个 Linux VM

这两天需要给出一个具体细节的 task 步骤，和 Yanqin 过一下

明天过来之后也想要了解如何给自己在 EADP-JIRA 上给自己开个 ticket，追踪自己正在做的事情

明天还需要至少解决剩下两个问题中的其中一个




