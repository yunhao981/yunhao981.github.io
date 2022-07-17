---
title: java-spring-boot-3
categories: Java
tags: Java
description: Spring in Action Ver.5
show: true
date: 2022-07-17 16:55:00
---

## validation error

import javax.validation.* 会失效，原因是 Spring Boot 在 2.3.0 以后就不再默认包含在 web-starter 里面了

在 pom.xml 里加上了相关的依赖 = =

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
</dependency>

<dependency>
    <groupId>javax.validation</groupId>
    <artifactId>validation-api</artifactId>
</dependency>
<dependency>
    <groupId>org.hibernate.validator</groupId>
    <artifactId>hibernate-validator</artifactId>
</dependency>

```

明天看下第四版里面 spel 表达式的部分

稍微调整了下 IDEA 的 Run, Build 和 Terminal， 设置成窗口扔在另一块屏幕上，看起来舒服太多太多了

Alt + 4 RUN Window

Alt + F12 Terminal

Shift + F10 Run xxx

## WebMvcConfigurer no interface expected here

java: method does not override or implement a method from a supertype

一不小心把 implements 写成 extends 了……
