---
title: test-day-11
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-08-17 16:56:10
---
一早过来就碰到了 merge conflict，联系了 Yanqin 和 Dev 解决

merge pipeline 所使用的账号权限有点问题，所以没法删除多余分支，Kyle 解决了

也许还会有其他repo，但这回应该是没啥问题了吧

今天又可以去完善下如何解决conflict的那篇文档了

等待 nexus 的 merge 许可花了很久，就导致 regression 发起的时间极其晚

merge nexus -> stg nexus -> stg nucleus -> sanity check

就导致卡了非常久，sanity check 挂了一大片，也着实让我 insane

有一些细节的依赖事项，还是需要整理成文档，这样就明确许多

solr exporter pipeline 明天来写
