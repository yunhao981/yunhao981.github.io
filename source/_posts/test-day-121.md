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

### 3

我每天究竟在做些什么……

为什么在一个对 WLB 极度友善的环境下，我可以每天晚上熬到凌晨……

但也只是像以往一样，对着文档搭积木，同时又记不住太多细节

短期记忆几乎报废，只能抓住瞬间记录下来才不至于彻底忘掉

甚至思维的速度与深度都极度受限，希望这仅仅是岁月的侵蚀而不是劫后余生

最近甚至连对气味都不敏感了，大抵是对于未来的焦虑与不安吧

唯一的安慰是，看到 IDEA 的 Dracula 主题还能闻到紫菜蛋汤的味道

淡黄色的部分自然是蛋液高温变性后的颜色，橙色的部分是胡萝卜和南瓜

而我又经常会为了解决当下心理上的困扰，去忽视现实中存在的更为迫切的问题

比如说现在凌晨三点为了理清楚思绪情愿不睡觉也要朝 github 上继续灌水

即便这些东西深埋在南极的冰川下，有朝一日终究会灌进水

也许这么干可以让我联通一小会四年前的自己和七年前的自己吧，听听他们是如何骂我的

工作至今半年有余，维护了半年的 Bash 和 Groovy，把他们移来移去，

却依然会在 git 同步仓库这件简单的事情上弄不清楚应当如何优雅完成

回过神来，想要写点东西都磕磕绊绊的了

四年前写过那么几个 commit 的 TS + Vue，甚至已经认不出那些青涩的 commit message 

只有在 clone 当年那个仓库的时候，看到一缕日出的 HDR

而我又在焦虑些什么，心中最深处的忧虑又从何而来

我的底气从何而来，应当如何重新构建内心的安宁？

太久不读书，自己照照镜子都会觉得面目可憎，几近失去对复杂信息的处理能力

肉体上的质量倒是猛增了 10 kg，全围在腰上了
