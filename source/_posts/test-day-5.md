---
title: test-day-5
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-08-09 16:25:15
---

第二周！

上午更新了Fastrun Daily Tracking，在 19539 发现了Fail to get Jenkins Job

随后类似的错误报了相当多，也许是磁盘写满了的缘故

接着看了看 fastrun.portal 的源码，虽说同样都用了react，但整个项目结构和官网上的井字棋教程完全不一样

后面还是需要多去读一读看看的

比如说异步回调这边我就完全摸不着头脑

中午休息时间做了道使用最小堆的题，还对照着自己常用的键盘用PowerToys修改了下按键布局

这样以后 Backspace 和退出 vim 的 insert 模式就不会因为肌肉记忆按错了

下午依旧在试着让 1-Box Run Full-Cycle

起初又一次遇到了Permission Denied的问题，

在Jenkins master上执行了Jenkins Job Add_Token

大概是 cygwin 下的 ssh-keygen 生成的 id_rsa.pub 地址并不在使用 powershell 生成的地址吧

cygwin 的位于 `/home/yunhaoliu/.ssh/` 下

ps 的位于`C:\Users\yunhaoliu\.ssh\`下

然后解决了权限问题之后，发现先前在 `~/.bashrc`中加入的各种 \<repo>_HOME 并没有被 export，每次在 Windows Terminal中开启一个新的 cygwin 标签页，都需要重新执行 source ~/.bashrc，大概是需要写进win系统设置的path里吧

kanas 和 paragon 都在 nucleus 的 repo 里

随后遇到了 build catalog failed 的问题，

翻了翻log，发现是用 python 3.9 去执行了 2.7 的脚本

才想起来在安装 node 的时候，为了从源代码编译 node， 自动安装了 3.9.6，临时卸掉吧

现在用的是lts，不急着更新

大概从三点半开始在本地 One-Box 里面执行了 Build-Nucleus 和 Build-Catalog

Catalog花了25分钟，Nucleus估计要挂着一晚上了

稍微有点点担心超时，下班前是 build 不完了

check了若干 url-list群组里面的 jenkins job url

明日版本是 CHG0150416-CD-Regression

看看我再可以多做些什么？
