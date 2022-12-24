---
title: test-day-135
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-03-09 18:16:35
---
## Today's Task
- [ ] Investigate on Sox Audit Code and Cassandra

## Additional Task 
- [x] Saola Kafka Release Support
- [x] Nucleus Liquibase Cassandra on AWS Image Support
- [x] Learned how to update ChromeDriver Version on Web Hub from Peter Xin

## Thought

### 1

Web Hub 上 ChromeDriver 的版本需要人工手动更新，万恶的 Google Auto Update

它会自动更新 Chrome 版本，而 ChromeDriver 版本必须和 Chrome 匹配

selenium/lib 下的 chromedriver，下下来的新版本先拖进去一份备份，后缀是版本号

然后再替换掉原来的那份 chromedriver

Chrome 没法固定住版本，在 Win 下用 Chrome 跑也是为了测试的时候更贴近用户使用场景

毕竟没有神仙会从 Linux 用 Chromium 访问……
