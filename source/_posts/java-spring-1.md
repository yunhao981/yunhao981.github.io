---
title: java-spring-1
categories: 读书笔记
tags: Books
show: true
date: 2022-07-13 13:10:31
description: Spring in Action Ver. 4
---

# 2. (装)配 (B)ean

声明 Bean

构造器注入

Setter 方法注入

装配 bean

控制 Bean 的创建和销毁

装配 创建应用对象之间协作关系

显式：xml 配置，java 配置

隐式：自动装配机制

## 自动装配 Bean

组件扫描 Component Scanning

Spring 自动发现 AC 中创建的 Bean

自动装配 Autowiring

Spring 自动满足 Bean 之间的依赖

## 样例

定义接口，降低耦合

```java
public interface CompactDisc {
    void play();
}
```

提供一个接口的实现

`@Component` 注解，告知 Spring 为它创建 Bean

`@Component("lonelyHeartsClub")` 可以给 Bean 命名

```java
@Component
public class SgtPeppers implements CompactDisc {
    private String title = "Sgt. Pepper's Lonely Hearts CLub Band";
    private String artist = "The Beatles";

    public void play() {
        System.out.println("Playing " + title + " by " + artist);
    }
}
```

用 `@Configuration` `@ComponentScan` 启用组件扫描

```java
@Configuration
@ComponentScan
public class CDPlayerConfig {

}
```

测一把

```java
@RunWith(SPringJunit4ClassRunner.class)
@ContextConfiguration(classes=CDPlayerConfig.class)
public class CDPlayerTest {
    @Autowired
    private CompactDisc cd;

    @Test
    public void cdShouldNotBeNull() {
        assertNotNull(cd);
    }
}
```

@Autowired 可以用在构造器和 Setter 上

当 Spring 创建另一个 Bean 的时候，会通过这个构造器实例化，传过去一个可以设置的 Bean
