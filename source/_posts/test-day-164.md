---
title: test-day-164
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-07-15 10:50:47
---
## Today's Task
- [x] Docker remove local image script
- [ ] Adjust CTS release pipeline default version 

## Additional Task 
- [x] CP image & deploy
- [x] nucleus, nexus, shadowbroker create branch for 8574
- [x] tag yesterday afternoon's cm regression & wiki page update

## Thought

昨天第三章看得属实云里雾里

今天再仔细看下它想说些什么吧

上周五清了 50 GB 的历史 image，因为需要确认安全，是手动 docker rmi -f 的……

这回花10分钟撸了个 script 去通过关键词找 container id，然后直接对着找出来的列表循环删 image

毋庸置疑，快多了
