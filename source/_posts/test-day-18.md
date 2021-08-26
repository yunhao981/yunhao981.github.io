---
title: test-day-18
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-08-26 18:46:58
---
一早过来之后，porpoise 的 MR 已经 Approve 了

于是 build image 测试了下，pass

那么这个 pipeline 的修改分支 MR 也能被 Approve 了

今天的 cut 里面发现 Code-Merge-Pipeline 在执行 merge 之前并不会 diff

也就是说它并不会确认要合并的目标分支和当前分支之间的差别

就导致了新的改动并没有更新进去，后来在 bash 脚本的语法上纠结了非常长的一段时间

最终是通过 git diff 的输出有没有 + 或 - 来判断有没有 change，临走前提了个 MR，Approve 了

然后玩了会 EADP JIRA，给 fix pipeline 做了个补充 work log

大概这个任务就结了

下午收到了邮件，记录着不同部分的具体 Owner 和 Backup，要熟悉一下 emergency flow 和 drive test sign off

昨晚再一次确认了 component audit pipeline 的细节，但是要修改的还是有很多，明天来做这件事情

在今天确认 Get Component 的时候，发现在它给出的 Component 列表以外，仍然需要人工去确认 gitlab

也就是说这个和 component audit pipeline 没有啥关联是吧，明天需要确认

明天需要 focus on component audit pipeline 的 Console output 整理

事情很多，需要排优先级顺序

写日记的时候发现 KB212 反应有些慢，主要是回弹和按键触发力度上，有点跟不上自己