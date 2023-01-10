---
title: java-tips
categories: Java
tags: Java
description: Java Tips from LeetCode Books
show: true
date: 2022-12-12 01:00:14
---

# Day 1

## 1. 接口与抽象类的区别

|   | 接口 | 抽象类 |
| - | - | - |
| 方法 | 抽象方法 | 抽象方法和普通方法 |
| 关键字修饰 | implement | abstract |
| 定义常量变量 | 静态常量 | 成员变量 |
| 子类方法 | 所有方法 | 抽象方法 |
| 子类继承 | 多继承 | 单继承 |
| 构造方法 | 不可以有 | 可以有 |
| 接口实现 | 只能继承接口，不能实现 | 可以实现接口，可以不实现接口方法 |

## 2. 继承与 C++ 的区别

Java 类只能单继承，C++ 可以多继承

C++ 子类可以有两个以上父类

## 3. Java 数据结构，HashMap 底层实现

Array, LinkedList, Stack, Queue, Stack, Tree, Map ...

1.7前用的是数组与链表， 1.8 之后用的红黑树

红黑树 ... ?

## 4. Java 用的是值传递还是引用传递

值传递：传递对象的副本，复制一份实参的值给形参

引用传递：传递对象的引用，复制实参的地址给形参

说法1: 对象传递是引用传递，原始数据类型是值传递

说法2: 值传递

对象：Array, Class, Interface

原始数据类型: Integer, Float, String, Boolean

## 5. final, finally, finalize

final: `static final foo = "bar";` 常量必须附初值且不变

finally: try { ... } catch { ... } finally { ... }

finalize: `java.lang.Object.finalize()`, 允许回收未被使用的内存垃圾 

## 6. 序列化，反序列化

序列化: 对象 -> 字节序列, 用于存储与传输

反序列化: 字节序列 -> 对象

Hadar 连 DB 的时候加上的一通 Jackson 就算是一个例子（虽然实现的很难懂）

## 7. 不可变类

实例的属性不可修改的类

不可变类的实例对象从创建出来之后，成员变量不可被修改

比如说 String 和基本类型的包装类  

更安全一些

## 8. 为什么 String 是不可变类

1. String 类的三个属性都是 private 而且没有修改数值的方法

2. String 类的三个属性都是 final

3. String Pool , 创建 String 时如果字符串值在 String Pool 里面就会返回已经存在的 String 的引用，如果 String 可变，其它引用这个字符串值的 String 值会变

## 9. API，SPI

API：实现方定义与实现的接口

SPI：调用方制定的接口

# Day 2

# Day 3

# Day 4

# Day 5

# Day 6

# Day 7

