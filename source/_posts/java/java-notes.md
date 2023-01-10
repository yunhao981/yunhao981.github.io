---
title: java-notes
categories: java
tags: java
description: java 豆知识
show: true
date: 2021-09-07 14:14:24
---
# 两个花括号？

外面一层是一个继承特定类的匿名类，

里面一层是 initializer

```java
new ArrayList<Integer>() {{

    add(1);
    add(2);
}}
```
