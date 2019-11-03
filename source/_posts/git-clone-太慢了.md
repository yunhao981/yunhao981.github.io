---
title: git clone 太慢了
show: true
date: 2019-11-04 02:46:38
categories: GitHub
tags: GitHub
description:
---

git clone 实在是太慢了

均速 10 KiB/s 龟速拖仓库

保证本地配备了超音速机场，可以让他乘✈️

机场设置 socks5 代理，会得到本地监听地址和端口,这里本地地址 127.0.0.1， 端口1086

~/.bashrc 中加入

```bash
alias fg="git config --global http.proxy 'socks5://127.0.0.1:1086' && git config --global https.proxy 'socks5://127.0.0.1:1086'"

alias ufg="git config --global --unset http.proxy && git config --global --unset https.proxy"
```
然后 
```
source ~/.bashrc
```
就可以在通过 fg 设定 git 代理，使用 https 拖仓库的时候乘飞机了。但 ssh 方式拖的时候是没办法加速的，需要给ssh设置代理。

ufg 是取消设置代理。




