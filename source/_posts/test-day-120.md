---
title: test-day-120
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-02-16 11:49:41
---
## Today's Task
- [ ] Property Page
    - [ ] Search History in Local Storage

## Additional Task 

## Afterwork Task
- [ ] Try Ktor HTTP API Demo
- [ ] Read about Kotlin Coroutines

## Thought

### 1

CKLT:

- [x] access
- [x] catalog
- [x] crypto
- [x] customerportal
- [x] dynamic-config-ui //need nucleus
- [x] hyas
- [x] kakapo
- [x] keymaster
- [x] nam
- [x] nexus
- [x] nucleus  //17GB source code
- [x] nucleussolr  //need nucleus
- [x] playercard
- [x] playerownership-cassandra
- [x] playerownership
- [x] porpoise
- [x] saola
- [x] sloth
- [x] tos
- [x] vaquita


### 2

git Q&A

1. 每次同步打出 commit 的目的

同一个 branch 会有不同的 commit

需要具体的 commit id 来确认改动

同一个 branch 在同一时刻指向的 commit 是确定的，一定是当时的 top commit

但是在之后如果有新的 commit 进去了，就不能确认这时候的 branch 里面是不是多了不需要的 commit

2. 带上 tag 的好处

tag 用来标记某个 commit

对于 Jenkins 来说有点奇怪

但对于人类可以更加直观

可以知道在某个确切的 commit 的时刻，当时这个 branch 里的内容是什么，而不是当时做了什么

branch 总是指向 top commit，而 tag 不会变

2. pull 和 fetch 的区别

git fetch 会去拿新的改动 metadata，然后也会下下来改动的文件

fetch 不会动到自己的 branch，

pull 会把 origin 同名的分支合到本地分支

如果 origin 没有同名分支或者冲突的话，行为就不知道了

3. 只用 git checkout ${branch} 的问题

同名的 branch 如果本地也存在，它就不会去同步 origin 的更新

比起 checkout 完了再去 merge origin/${branch}

更好的办法是 

checkout -f 强制切换到目标 branch，丢掉当前 local change

4. git fetch 的问题

remote branch 如果删掉了，本地指向这个 branch 的 refs 也需要处理掉

所以需要再去 prune 一次

`git fetch --prune`

相当于

`git fetch --all && git remote prune`

会在 prune 之前，从 remote 拿一下最新的状态

5. git push --force-with-lease

force 强行把本地分支推上远端覆盖掉

force-with-lease 不会覆盖远端分支里面别人加进去的 commit
