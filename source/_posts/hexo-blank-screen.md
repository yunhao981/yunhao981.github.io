---
title: hexo-blank-screen
categories: hexo
tags: hexo
description: hexo 白屏
show: true
date: 2021-10-30 09:52:04
---
心血来潮想要给 hexo 换个主题

顺便解决 github 一直在网页上的报错

然后就炸了……

不知道是 package.json 里面的问题

还是一些奇怪的设定所致

本地可以成功地 hexo s

`No layout: index.html`

也许这个才是真正的原因？

然后发现主题没有到 github 上

所以 travis ci 没办法生成 index.html

github 上 clone 到 themes 下的主题，需要设置成 submodule

而且 url 用 https 会比 ssh 更稳妥…