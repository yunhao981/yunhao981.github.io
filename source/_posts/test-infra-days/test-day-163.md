---
title: test-day-163
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-07-14 15:29:09
---
## Today's Task
- [ ] Docker remove local image script
- [ ] Adjust CTS release pipeline default version 

## Additional Task 
- [x] Recut nucleus
- [x] new INT CM cut build, deploy & regression 
- [x] cp, v5, build & deploy from test branch 

## Thought

测的时候发现之前那十几个 repo 的 script 全都改炸了…

每个问题都还不一样…

有些是路径配的有问题，有些是尝试去删了一个莫名其妙的 Docker image id

CP 有时候容易跑不起来或者 build 不过

这个时候需要去 nova utility 上 mvn clean install 一趟 dodo 
