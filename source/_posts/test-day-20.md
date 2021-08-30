---
title: test-day-20
categories: test
tags: test
description: 周五的 pipeline 有 bug，修好了
show: true
date: 2021-08-30 17:31:13
---
周五的 merge pipeline 有 bug

今天在用的时候，发现只执行了一半就跳过去了

releases/rel551 这个分支下完全没有更新

后来还是用的 master 分支救急

接着发现如果直接 grep 的话，它会停在 grep 到目标之后就跳去下一步了

甚至最终还是个 success

然后下午又是一通面向 google 和 StackOverflow 编程

终于是找到了在 Jenkins file 里直接操作 console log 的简单办法

```groovy
def bar = ""
def foo = sh(
    returnStdout: true,
    script: "bash xxx.sh"
)
def arr = foo.split("\n")
arr.each {
    if (it.contains('target')) {
        bar += it
    }
}

```
像这样就可以找到包含目标字符串的一整行，而且不怕重复出现覆盖掉先前的结果
