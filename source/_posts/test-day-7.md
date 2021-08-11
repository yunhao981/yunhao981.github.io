---
title: test-day-7
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-08-11 21:19:27
---
今天居然改了一整天的 build.sh

只是为了修改 build image 的 release version pattern 就找了半天

对应的时间戳生成的方式完全不一样

还有 CHG number 一开始压根就没有这个参数

甚至还涉及到了 binary release version

压根找不到对应的生成位置

但是引入了新的参数，可能会影响到 Loadtest，所以明天来需要再重新看看

下午晕乎乎的，大概是中饭GI值太高太高了，明天吃河粉或者 wagas 吧

办公室楼下一楼就有一家吃草的店，明天可以试试看

后来还解决了 code-merge-pipeline 的 token 问题

真的就藏在 /var/lib/jenkins/super_secret 里面

然后正式接到了一个新的 issue

需要 fix 一个名为 fast-liquibase 的 Jenkins job

可能是 wget 的命令出错了，也可能是找不到对应的文件，甚至搞不好还是一个 token 问题

我记得之前说是有个网站处在生死边缘，好像正是 artifactory？还是啥别的

反正后来发邮件问了

实在不行的话就还需要多问问 Yanqin Chen 了

还是挺怀念当时实习的小公司，四个人人均 root

