---
title: test-day-77
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-11-29 10:18:19
---
## Today's Task
- [ ] Add a page to search properties on ReleaseMe
    - [x] Rebooting backend but failed on 8080
        - [x] solved by checking yml urls
    - [ ] Frontend page
- [x] Delete comments (only current users')
    - [x] Add DELETE APIs on comments to backend
        - [x] Get familiar with Spring Boot
        - [x] SQL in CommentInfoMapper
        - [x] convert in DAO
        - [x] API in Controller
    - [x] Frontend Button
- [ ] Transfer Jenkins Jobs
    - [x] Double check script typo
    - [x] Run CP One Case Successfully
    - [x] Run RL-CP-BVT Successfully
    - [x] Run Master_Lockbox_OneCase
    - [ ] Run Master_Lockbox_BVT
    - [ ] Move all the other jobs
    - [ ] Test all the other jobs
- [ ] OneBox-Setup vmip
    - [ ] Deploy with nginx and docker
        - [ ] Get familiar with nginx
        - [ ] Get familiar with dockerfiles
- [ ] Help Song Chenxin to change image tag pattern

## Additional Task 
- [x] Upgraded Jenkins on Slave1 from `2.150` to `2.222.4` to use `Rebuild` and `Trigger Job` plugin

## Thoughts

周五 James 解决了slave1访问很慢的问题

看着像是 log 太多了，清掉就 ok 了

上午的半个小时相当紧张，Jenkins 更新失败了

最可怕的是降级回原来的版本会报新的错误

爬了 20 分钟的 Stack Overflow

设置了参数，调整读取 config 的时间

终究最有用的解决方案还是降到一个中间的版本

中午刷了一题 leetcode 

是不是可以早点起床吃早饭，早点骑车带着笔记本去到什么地方自己学点东西？

昨晚 8 点睡到了 1 点，随后又从 4 点睡到了 8 点 45

今晚试试 10 点多睡，醒来如果天亮，先直接爬起来吧

下午照猫画虎写了 ReleaseMe 删评论的 api

然后开始在前端用 ts 写 bug
