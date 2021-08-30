---
title: test-day-19
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-08-30 17:31:06
---
改了一整天的 code merge pipeline

终于是能够成功获取到 Jenkins file 里某一行特定脚本的输出了

原先是 sh "xxx" 的，其实这里 sh 相当于一个函数

然后就需要写成

sh(returnStdout: true, script: "xxx")

才可以把输出的内容保存成 string

随后用了 grep 去找里面是不是包含某一个特定的字符串

而为了做这件事情居然花了我五个小时，还是因为不熟悉 groovy 和 Jenkins 吧

在 Jenkins file 里写 lambda 遍历 map 是我最后的倔强