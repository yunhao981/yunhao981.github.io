---
title: test-day-221
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-10-12 17:40:46
---
## Today's Task

- [x] Fix Catalog Clear DB semi-auto pipeline
- [x] Add Nexus and Catalog support to Component Audit v4
- [x] Upgrade Sanity Jenkins to support post build scripts
- [x] Fix common template branch for shared library
- [x] Fix Catalog support for slack notification bot

## Additional Task 

- [x] Deploy Nucleus to AWS STG

## Thought

Jenkins 升级前千万要记得备份整个目录

备份完了之后先升级所有的插件

然后停掉进程，再去换 jenkins.war
