---
title: java-spring-4
categories: 读书笔记
tags: Books
description: Spring in Action Ver. 4
show: true
date: 2022-07-18 12:50:25
---

# Spring Web App

- 映射请求到 Spring Controller

- 透明绑定表单参数

- 校验表单提交

Model View Controller

## Spring MVC 起步

调度 Servlet，Handler Mapping, Controller, View Resolver

Spring 会将请求在上述几个之间移动

Request -> DispatcherServlet -> Handler Mapping -> Controller -> DispatcherServlet -> View Resolver -> View -> Response

### 1. Requset -> DispatcherServlet

Spring MVC 所有请求都会通过 Front Controller Servlet， 也就是 DispatcherServlet

DispathcerServlet 会把请求委托给其他组件处理

### 2. DispatcherServlet -> Handler Mapping -> Controller

DispatcherServlet 会去查询 Hander Mapping 决定将请求发到哪个具体的 Controller

通过 URL 决定

业务逻辑一般交给 Controller 去处理

Controller 会去处理 Request Payload

### 3. Controller -> DispatcherServlet

Controller 处理完 request 之后会有产生额外的信息，返回给用户显示在浏览器上

这些信息便是 Model

View 用来把原始信息处理成用户友好的格式, HTML

Controller 会把 Model 打包，连同 Request 和 View 名字一起发给 DispatcherServlet

### 4. DispatcherServlet -> View Resolver -> View 

DispatcherServlet 收到的只是 View 的名字，所以可以用 ViewResolver 去通过名字找到真正对应的 View 实现

### 5. View -> Response

DS 把 Model 数据交给 View 实现完之后，请求就结束了, 

View 会用 Model 数据来渲染输出，把 Response 交到 Client

