---
title: test-day-43
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-10-12 17:11:37
---
今天踩的坑：

## component audit 运行 git fetch 超时

改了 timeout 从 60 到 120，让 repo 可以被 clone 下来

## lockbox-cp merge conflict

虽然知道 99% 都会用新的那个改动

但还是需要去问 Owner 来确认以保证没有潜在的问题

最最起码也要让他们能够知道这件事情

## build image 参数填错

同事多填了一个空格，我乍一眼还看不出

好在 git tag 报了个错

## guardiola, vaquita 0 change

Manually check GitLab to ensure that all changes in CHG branch are merged by Jenkins Automation Server before.

Disable 'Check Change' in code-merge pipeline, and try again.