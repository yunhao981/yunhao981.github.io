---
title: test-day-15
categories: test
tags: test
description: fix pipeline step 1, OneBox Setup Debug
show: true
date: 2021-08-23 18:06:27
---

手上有三个任务，一下子有点不知所措

比起每天每个任务都推进一点点而言，更希望每天可以直接解决一个

今天在 Yanqin 的帮助下准确地在 Artifactory 上找到了不同 CodeRepo 所对应的 liquibase.data ， nexus 的是 liquibase.data.cassandra

然后就是在 mysql-deploy.sh 里面直接判断是哪个 repo 了

还是在 artifactory 上翻了好久，甚至还没完全找到每个 repo 各自分别在哪里

明天来也许可以解决这个 404 的故障，而另一个还得再看看会不会复现

Onebox setup 页面的 bug 今天还没成功复现出来，说是在不同的选项选中时，生成的编译命令会出错。也许和页面生命周期和 state 有关联，还涉及到了 hook 和 refs

其实完全不懂，回家还得恶补