---
title: test-day-46
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-10-15 18:47:26
---

写了 porpoise.cassandra 和 ibex.cassandra 的 pipeline

测试的时候遇到了非常多的坑，弄了一个下午

首先不能直接放在 registory Jenkins 上，因为这样就相当于没测直接上线

registory 在这里没法访问

但依然需要本地测，所以要让做出来的 image push 到 eadpciregistory, 相当于是 cn 的镜像站？

registory 上有的东西，cn 上没有，好在有替代方案

为了运行 script 需要 docker，当然还需要 ibex 的源码

然后本机有源码没 docker，虚拟机有 docker 没 Onebox 环境

借来的 Onebox 无法 clone 源码，最终是 scp 上去的

执行完之后发现结果和 registory jenkins job 上的不一样

发了邮件问 Rahil，希望周一可以得到解答

以及 PCI 权限申请的后续，为了确认 staging env

fastrun 的某些机器 （245之类的），VBoxManage poweroff 关不掉

这是造成超时的直接原因

然后发现其实还在跑，甚至可以 ssh 进去再一次 poweroff

然后发现仍然在跑，但没法 ssh 进去了

也不知道上回他们怎么解决的


