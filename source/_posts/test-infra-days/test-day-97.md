---
title: test-day-97
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-01-07 10:17:13
---
## Today's Task
- [x] Hotfix CM Release Support

## Additional Task 
- [x] Check component audit, component audit v4, audit tool with cm-release
- [x] ask ops to create missing repositories on CIAWS
- [ ] fix email sending issues of v5 INT BVT
- [x] fix component_audit using cm-relese and full-cycle/dumb-librarian
- [x] fix audit tool
- [x] check nucleus liquibase update manually
- [x] Varify citadel prod image version
- [x] Check missing components on wiki page
- [x] Trace Sanity Check Failures
- [x] fix vaquita js heap out of memory

## Thought

### 1

常用的 job 移到了 cm-release 里，对应的设置需要修改

要确认原先不同 private branch 里的改动是不是都进到 master 了

dumb-librarian 移到了 full-cycle 里，incremental build 会用到