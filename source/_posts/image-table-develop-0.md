---
title: image-table-develop-0
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-09-08 17:06:00
---
# 从哪里获取 image ？

直接从 release image 的 Jenkins job 里面抓 Successfully tagged ... 即可

或者从这个 pipeline 本身开始触发 build，然后汇总所有 image tag 到一起



# image 的存储形式？

只需要 tag，不需要本体

所以一张表就 ok

并不需要考虑最大容量 4GB 的 LONGBLOB

| id | chgnum | component | imagetag |
| - | - | - | - |
| 0 | CHG0150424 | nucleus | commerceprovision:551.0.210909.451.28f2606.202109090654.CHG0150424_3rd_cut.1631170495

# 需不需要用 java 写？

只需要存 tag 当然不需要这么麻烦

# 如何与 mysql 交互？

bash 脚本上命令？

# 如何解决 recut

To be continued...