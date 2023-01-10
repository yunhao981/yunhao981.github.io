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

# 3. 往自己分支拉一把 master

```bash
git rebase master
```

用 rebase 而不是 merge （洁癖星人

# 4. git fetch 与 git pull

git fetch 会去拿 metadata，但不会动本地文件

git pull 会在拿好 metadata 以后，改动本地文件

# 5. 合并一些 debug 过程中的 commit

git rebase -i ${要合并的起始位置的上一个 commit}

然后把第二行开始的 pick 全部改成 s 

接着改下 commit messages

git push -f
