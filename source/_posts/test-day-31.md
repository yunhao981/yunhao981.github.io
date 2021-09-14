---
title: test-day-31
categories: test
tags: test
description: 大红灯笼高高挂
show: true
date: 2021-09-14 18:09:42
---

今天的 cut build 发生了非常多的意外...

从一早的 merge 开始，其实并不需要保留原有分支，merge 的行为是正常的，差点以为自己误删了分支，有点吓人

随后遇到了server no space left，服务器磁盘容量不足，也许可以直接问问 Jen ？就不用发邮件问 24x7 了

磁盘空间不足的问题导致了 image build 非常拖慢，连带着后面的 STG 和 regression 都没法按时执行

以及 checklist 小表格用起来有点麻烦，挺慢的其实

STG 前需要等 ESS 更新，不然会报证书相关的错误

另外 paragon 的 image build 碰到了 x509 certificate signed by unknown authority

是一个相当奇妙的玄学问题，问了 Jen，It worked fine on his machine when running build script manully.

然后经过了三次失败以后的第四次尝试，在 Jenkins 上倒也能正常执行了

sanity check 全线飙红，Zhong Lu 问了一大圈，几乎是还留在办公室里的所有人

然而依旧是大红灯笼高高挂



