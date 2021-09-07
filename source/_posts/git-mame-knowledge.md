---
title: git 豆知识
categories: git
tags: git
description: 用 git 的时候碰到的坑
show: true
date: 2021-09-07 11:13:14
---

# 1. 想要撤回 Amend Commit

```bash
git reset --soft HEAD@{1}
git commit -C HEAD@{1}
```

# 2. 分支命名有点冲突

报错大概长这样
```
error: cannot lock ref 'refs/remotes/origin/release': 'refs/remotes/origin/release/430' exists; cannot create 'refs/remotes/origin/release'
 ! [new branch]   release -> origin/release  (unable to update local ref)
```
```bash
git remote prune origin
```