---
title: java-spring-3
categories: 读书笔记
tags: Books
show: true
description: Spring in Action Ver. 4
date: 2022-07-15 13:51:01
---

# 4. 面向切面的 Spring

- 面向切面编程的基本原理

- 通过 pagp创建切面

- 使用 @AspectJ 创建注解

- 为 @AspectJ 切面注入依赖

横切关注点 Cross cutting Concern: 散布于应用中多处的功能

AOP想要解决的问题把这些横切关注点和业务逻辑相分离

切面实现了跨多个应用对象逻辑的模块化

## 4.1 AOP 是啥

### 通知 Advice 

切面的 What 和 When

定义切面是什么，何时使用

可以应用五种类型

- 前置通知 before

目标方法调用前通知

- 后置通知 after

目标方法完成之后，输出无所谓

- 返回通知 After-returning

目标方法成功执行之后，成功执行

- 异常通知 After-throwing

目标方法抛出异常之后

- 环绕通知 Around

通知包裹被通知方法，包起来，调用之前和调用之后执行自定义行为

### 切点 Pointcut 

切面的 Where

### 连接点 Joinpoint

应用执行过程中插进切面的点

### 切面 Aspect

 通知 + 切点

### 引入 Introduction 

朝现有的类添加新方法或者属性

### 织入 Weaving

把切面应用到目标对象，创建新的代理对象

## AOP 支持

Spring 提供了四种类型的 AOP 支持

- 基于代理的经典 Spring AOP

- 纯 POJO 切面

- @AspectJ 注解驱动的切面

- 注入式 AspectJ 切面

这些概念没看懂 = =

看看具体的示例代码可能心里就会有数了
