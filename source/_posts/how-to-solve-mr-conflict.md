---
title: 如何解决 git 合并冲突
categories: test
tags: test
description: 磨人的 merge conflict
show: true
date: 2021-08-16 15:08:56
---
同一个文件的同一行，被不同的人修改成了不同的样子

或者是修改了一个文件，另一个人删掉了它

那就不知道哪个才是正确的选项了，到底需要保留哪一个？

如果是自己的项目，个么总归自己决定咯

自己写的东西还能搞出 merge conflict 的也是精分现场了

如果是工作里碰到的，问 Owner 让他们决定留哪一个

总归是能知道要把冲突的文件怎么改的

直接进项目目录，比如说

`/home/root/code_merge/${repo}`

对于 testinfra-master 这台机器上的 code-merge pipeline，

需要用 root 权限来做这些事情

`git status` 看看哪个文件冲突了

如果 pipeline 报错但是 status 没的话

就手动 `git checkout release` 之后 `git merge CHGxxxx`

然后在对应冲突的文件里找到提示冲突的一大堆箭头

想好怎么改了以后删掉 `<<<<<<<`, `=======`, `>>>>>>>`

然后 `git add .` 或者直接 add 改动的文件

`git commit -m "Resolved merge conflict by xxxxxxx"`

最后再 merge 或者直接 push 就好了
