---
title: test-day-96
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-01-06 10:18:41
---
## Today's Task

### ASAP:
- [ ] Add comment time to ReleaseMe
- [ ] Add a page to search properties on ReleaseMe
    - [ ] Router without React Router
    
### Daily Pushing
- [ ] Transfer Jenkins Jobs
    - [ ] RLCP-BVT

### Not so urgent
- [ ] Add all components to Create-emergency-branch
- [ ] Split CheckSTG

## Additional Task 
- [x] Build Shadowbroker Cassandra image
- [x] Make a pipeline for shadowbroker cassandra
- [x] help to deploy image for customizedlog-esv6grn
- [x] add .idea to .gitignore
- [x] fix porpoise and hyas liquibase.data version tag


## Thought

### 1

凌晨一点睡下去

四点钟饿醒我没想到……

煮了泡面之后，后面也没有睡着

今天组会晕乎乎的

在回想自己需要做的事情的时候，是真的见到了白色的画面

ETA 一周的 feature 要快点做完

活用 JIRA Kanban Board

需要自己设置 DDL

### 2

自己开的坑终于成为了 maintainer， 可以做一些各种各样的事情了（比如说加入 pipeline 支持

IAD2_JumpTools_PCI -> jussh -> select stg -> select container -> You're in the container now

这一层的 Deploy image 问 Ops，我们负责的是 K8S 的那些

### 3

porpoise.liquibase.data 的 tag 格式有问题

ReleaseLBPorpoise -> Upload Binary

`Code2ImageJenkins.groovy` -> `build.sh` -> `generate_porpoise_new.sh` -> `build_common.sh`

最后发现是 `release.sh` 里面，把 Version 按照小数点 split 成了一个数组，然后手动取前四个，再组合回去

把丢掉的第五项补上了

### 4

迁移 LB Jenkins Job 到一半，

原来的服务器，硬盘挂了

slave 1 上 /usr/lib/jvm/zulu-8 从28号开始找不到，做了个符号链接…

看了眼 history，java 全删了…… 只留了一份在 shdev 家

重新配了下 `$JAVA_HOME`

又查出来两个 Post Script 里的 bash 脚本错误

另外还有各种 Repo 的本地路径配置

希望今天可以跑通 INT BVT