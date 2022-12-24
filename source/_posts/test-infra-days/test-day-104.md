---
title: test-day-104
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-01-18 10:12:05
---
## Today's Task
- [ ] [ASAP] Property Page

## Additional Task 
- [x] Remove service worker
- [x] Port Catalog Release Script to CM-Release
- [x] Fix RleaseMe Frontend ENVs

## Thought

### 1

Jenkins pipeline 里面，SCM 虽然可以设置很多个 repo

但似乎并不能让每个 repository checkout 到 不同的 branch 下

原本 release image 脚本就在当前 workspace 里，所以其实只需要指定一次 branch 就可以了

但是集中移到另一个 repo 里之后，

终究还是用 bash 脚本手动 git 了