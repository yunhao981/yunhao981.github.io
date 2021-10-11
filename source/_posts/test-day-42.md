---
title: test-day-42
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-10-11 18:23:37
---
audit 步骤时没有发现 saola.kafka 的更新

所以漏掉了它的 image

三个 job 里有问题导致没有找出来

sox audit: 和钱相关的很少几个

component audit: products in Nucleus Repo

component audit v4: General

问题出在 component audit v4 里面？

release runbook 上 saola.cassandra, kafka, zookeeper 是三个独立的 Product，而它们在 v4 里被当作是 saola 的一部分对待，并不知道有更新

//有个commit包含非文本的改动导致被当成了 0 change

merge 成功了，但涉及到的 Component 没有 build image

audit 的时候只说 saola 有改动，但没有提示 saola.infra 下的几个 component 各自是不是有改动

加上这些对应的判断，hard-code 也没问题

v4 里面，只判断 change 的字数，甚至还是 byte count

在确认有改动之后，用 git diff 来找改动对应的文件

如何测试改动的结果？

建立了测试分支，而 v4 判断的是 merges to branch 里的 file change

我需要两个测试分支，一个改动，另一个作为 merge 目标

本地克隆下来试试吧

然后发现字符串匹配不上

if 少写方括号

大量的 if else，用 array 代替


