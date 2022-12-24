---
title: test-day-136
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-03-10 10:30:25
---
## Today's Task
- [x] Investigate on Sox Audit

## Additional Task 

## Thought

### 1

昨晚试着往 sox audit 里面加了几行 log.debug()

发现它并没有删掉任何一行 cassandra log

但是找到了 24497 条记录……

等下回 CM 再执行看看

### 2

发现 Jenkins Credentials 是有问题的…

如果通过 withCredentials 定义在 groovy 脚本的 top level 

在 step 里面 echo 可以直接拿到明文？？？

### 3

Groovy 里面的 def 额可以用来声明变量和函数，而类型会在运行时根据值来推断出来
