---
title: java-spring-0
categories: 读书笔记
tags: Books
show: true
date: 2022-07-12 12:52:21
description:
---

# Spring in Action Ver.4

目标：撸一个基础的传统 Spring 项目，也许大概花 2~3 周左右？一天一章

4 和 5 对照着看可能会有更多收获

4 有更多基础概念，但版本会老一些

示例项目也并不同 (又可以水一个新项目了好耶

Spring：简化开发的某个开源框架

Bean: 约等于 POJO

POJO: Plain Old Java Ojbect 

DI: Dependency Injection 依赖注入

AOP: Aspect Oriented Programming 面向切面编程

AC: Application Context 应用上下文

# 1 Spring 之旅

策略

1. POJO， 轻量级，最小侵入性编程
2. DI与面向接口，松耦合
3. 切面，惯例，声明式
4. 切面，模板，减少样板式代码

## DI

好处：松耦合

如何实现？

方式一: 构造器注入 Constructor Injection 

把对象塞进构造方法的参数里面传过去，而不是在构造器里创建一个新的对象

装配：创建应用组件之间协作的行为

可以通过 xml 或者 java 描述配置

两者等价

```xml
<beans>
    <bean id="knight" class="com.springinaction.knights.BraveKnight">
        <constructor-arg ref="quest" />
    </bean>

    <bean id="quest" class="com.springinaction.knights.SlayDragonQuest">
        <constructor-arg value="#{T(System).out}" />
    </bean>
<beans>
```

```java
@Configuration
public class KnightConfig {
    @Bean
    public Knight knight() {
        return new BraveKnight(quest());
    }

    @Bean
    public Quest quest() {
        return new SlayDragonQuest(System.out);
    }
}

```

具体咋实现的还得去看八股文

先会用再说

有需要的话依赖注入可以详细去看 《Dependency Injection》 Dhanji R. Prasanna

AC 用来负责对象的创建和组装

## AOP

分离功能形成可重用组件

```xml
<beans>
    <aop:config>
        <aop:aspect ref="minstrel">
            <aop:pointcut id="embark"
                expression="execution(* *.embarkOnQuest(..))" />
            <aop:before pointcut-ref="embark"
                method="singBeforeQuest" />
            <aop:after pointcut-ref="embark"
                method="singAfterQuest" />
        </aop:aspect>
    </aop:config>
</beans>
```

## 样板式代码

比如说 jdbc 那一堆创建链接，捕捉异常，打扫战场的一套

## Bean

Spring Container： 创建对象，装配，配置，管理生命周期

Spring 容器的实现：bean factory 或者 Applictaion Context

常用的一些 AC 
```
AnnotationConfigApplicationContext
AnnotationConfigWebApplicationContext
ClassPathXmlApplicationContext
FileSystemXmlApplicationContext
XmlWebApplicationContext
```
## Bean Lifecycle

Spring bean 实例化

填充属性

BeanNameAware.setBeanName()

BeanFactoryAware.setBeanFactory()

AppplicationContextAware.setApplicationContext()

BeanPostProcessor.postProcessBeforeInitialization()

InitializingBean.afterPropertiesSet()

BeanPostProcessor.postProcessAfterInitialization()

准备就绪，可以用

容器关闭

DisposableBean.destroy()
``
