---
title: java-spring-boot-0
categories: Java
tags: Java
show: true
date: 2021-11-26 11:57:15
description:
---

```
你说我一个半吊子 DevOps,

怎么就跑去写 React + Spring Boot 了呢

很惭愧，做了些微小的工作
```

# Quick start

先从官方文档一脚踹进门呗

可以不用 deploy WAR files，就能直接支持 Tomcat, Jetty 或者 Undertow

简化 build configuration

自动配置 Spring 和第三方库

绝对不会生成代码，也不需要 xml 配置

start.spring.io -> Add dependencies -> Spring Web -> Generate 

即可得到 demo.zip

解压完了进 IDE 打开

冲进 `src/main/java/com.example.demo/DemoApplication`

```java
package com.example.demo;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class DemoApplication {

    public static void main(String[] args) {
    SpringApplication.run(DemoApplication.class, args);
    }
    
    @GetMapping("/hello")
    public String hello(@RequestParam(value = "name", defaultValue = "World") String name) {
    return String.format("Hello %s!", name);
    }

}
            
```
`./mvnw spring-boot:run` 就可以跑起来了

可以用 `curl localhost:8080/hello` 来确认

`@SpringBootApplication`：这是个 Spring Boot App

`@RestController`：这个 class 描述的是通过 web 可用的 endpoint

`@GetMapping("/hello")`： 用后面的`hello()` 来处理到 `localhost:8080/hello` 的请求

`@RequestParam(value = "name", defaultValue = "World")`: 需要一个名字叫 `name` 的参数，如果缺省的话默认值是 `World`


