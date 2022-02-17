---
title: test-day-121
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-02-17 10:23:40
---
## Today's Task
- [ ] Property Page
    - [x] Search History in Local Storage
    - [x] Two Tables
    - [ ] Rewrite it to be more pretty

## Additional Task 

## Thought

### 1

`2>&1`

2: stderr

1: stdour

&: 跟在后面的是文件描述符，而不是文件名

### 2

#### peer dependency conflict

```
15:08:39  + npm install
15:08:45  npm ERR! code ERESOLVE
15:08:45  npm ERR! ERESOLVE unable to resolve dependency tree
15:08:45  npm ERR! 
15:08:45  npm ERR! While resolving: release_me@0.1.0
15:08:45  npm ERR! Found: react@16.14.0
15:08:45  npm ERR! node_modules/react
15:08:45  npm ERR!   react@"^16.13.2" from the root project
15:08:45  npm ERR! 
15:08:45  npm ERR! Could not resolve dependency:
15:08:45  npm ERR! peer react@"^17.0.0" from react-mde@11.5.0
15:08:45  npm ERR! node_modules/react-mde
15:08:45  npm ERR!   react-mde@"^11.5.0" from the root project
15:08:45  npm ERR! 
15:08:45  npm ERR! Fix the upstream dependency conflict, or retry
15:08:45  npm ERR! this command with --force, or --legacy-peer-deps
15:08:45  npm ERR! to accept an incorrect (and potentially broken) dependency resolution.
15:08:45  npm ERR! 
15:08:45  npm ERR! See /root/.npm/eresolve-report.txt for a full report.
```

npm 7 以后会去看 Peer Dependencies 是不是和项目依赖冲突，如果冲突的话就会给 Error

--legacy-peer-deps 可以暂时不去管它，但终究是需要解决冲突的

