---
title: test-day-193
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-08-25 15:39:33
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

- [x] Send Failure tracking mails

## Thought

### 1
slack bot 发消息有长度限制，3000 B

会导致有时候 icon 没法更新

要么把消息拆开来，要么就再缩一缩

那 audit 和 merge 的消息算一条

build 单独算一条

deploy & liquibase 算一条


### 2

WakaTime Error，重设了 api key

VS Code Remote 真的好舒服

可以直接冲上 aws 一边写一边测 Slack Bot

配合 Nodemon 的话甚至可以 Hot Reload

感觉前几年折腾的 vim 插件比如说 NERDTree, Ctags 都用不上了。。。

### 3

axios post 和 get 的参数并不同

post 多一个 data
