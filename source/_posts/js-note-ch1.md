---
title: JS 笔记 第 1 章 什么是JavaScript
categories: 读书笔记
tags: JavaScript
description: JavaScript高级程序设计 第四版
show: true
date: 2021-08-08 00:05:04
---

第四版一周目

不要在浮尘上构筑高楼

# 1.1 简短历史回顾

对简单表单的输入数据验证脚本 -> 通用、跨平台、厂商中立的脚本语言

ECMA-262, ECMAScript 脚本语言标准

# 1.2 JavaScipt 实现

JavaScript

- ECMAScript
- DOM, Document Object Model
- BOM, Browser Object Model

## 1.2.1 ECMAScript

并无标准输入输出方法

宿主环境为其提供基准实现和与环境交互所需要的扩展

Web浏览器，Node.js，甚至Adobe Flash都是宿主环境

ECMAScript描述了语法、类型、语句、关键字、保留字、操作符、全局对象

ES6开始正式支持了类，模块、迭代器、生成器、箭头函数、期约（Promise）、反射、代理以及新的一些数据类型

ES8主要增加了异步函数和Atomics API

ES9修订了异步迭代、剩余和扩展属性

ECMAScript符合性，必须满足ECMA-262中描述的所有“类型、值、对象、属性、函数、程序语法与语义”，并支持Unicode字符标准

对于ECMA-262中并未提到的新对象和新属性，增加也可满足

也允许修改和扩展内置的正则表达式特性

## 1.2.2 DOM

文档对象模型，API，用来在HTML中使用扩展的XML，创建了表示文档的树

DOM level 1
 - DOM Core
 - DOM HTML

DOM level 2
 - DOM 视图
 - DOM 事件
 - DOM 样式
 - DOM 遍历和范围

DOM level 3
- Load and save
- DOM Validation

DOM4, Living Standard

## 1.2.3 BOM

浏览器对象模型，API，支持访问和操作浏览器的窗口

HTML5之前没有相关标准