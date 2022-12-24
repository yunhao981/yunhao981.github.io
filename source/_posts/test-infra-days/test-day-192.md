---
title: test-day-192
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-08-24 13:43:05
---
## Today's Task

- [ ] Build Script User Friendly Changes
  - [x] Extract Common Methods for PCT jobs
  - [x] Remove Audit Tool from old repo
  - [x] Extract Common methods for T1 image release scripts
    - [x] Catalog
    - [x] Nexus
    - [x] Nucleus
  - [x] Common methods for T3
    - [x] sloth
    - [x] vaquita
    - [x] cp
  - [ ] Common methods for T2

- [ ] Slack Bot
  - [x] run on AWS
  - [x] Try Demo Full Functions
  - [x] Basic Function
  - [x] Easter Eggs
  - [ ] New Features
    - [ ] Create temp CM modal & notification
    - [ ] Split modules

    

- [ ] Hadar Maintenance
  - [x] Hadar, failed job add console to url end
  - [ ] Hadar, failed job retry success, make slack message success

## Additional Task 

- [x] Resolve Merge Conflict in Nucleus
- [x] Fix clear catalog db job to exec prepareRole sql
- [x] Push v3 image to aws

## Thought

cm tool 的 api 有点奇怪

首先需要在 Header 里面带上 base64 的 `用户名:密码` 作为 Basic Authentication

然后会得到一个 Token, 请求其他 api 需要带上这个作为 Basic Authentication, 而不是 Bearer
