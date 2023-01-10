---
title: clear-catalog-stg-tips
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-03-13 22:35:32
---
# 啥时候需要做

每次 CM 铺 Cataglog STG 前

# 做什么

会用魔法登上 MySQL 删库

再重新创建一份新的

重启一下 pod

然后往里面塞很多数据

# 为什么需要

容易卡，导致别的 component regression 败一大堆

比如说 rating, commerce, subscription v2 三巨头

# 怎么做



# 坑

如果执行失败了，或者执行中止，需要手动从断掉的地方登上去执行

如果卡在删库那一步，不要中止，直接去重铺一次 catalog stg
