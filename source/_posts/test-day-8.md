---
title: test-day-8
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-08-12 18:07:44
---
更新了 Fastrun Daily Traking，听从James Qian的建议，把一些模糊的错误类型，进一步拆分成了更详细的错误

发现 check health 的问题还是很多

上午例会，对Fastrun究竟是什么有了比较简单的概念

Sync -> Build -> Deploy -> Test

Build test 和 Build Deploy 是并行进行的

下午修改好了 solr 的 image tag pattern，envName 暂时用 local

对于新的 issue，还是需要等待进一步消息

问了问 Yanqin， 有可能是 tar 在解压的时候出错了？

找不到tarfile

那么也有可能是 wget 这一步出错

和tarfile的文件名有关系？

明天再来看看更多细节，还要处理新版本的 cut
