---
title: java-spring-2
categories: 读书笔记
tags: Books
show: true
date: 2022-07-14 13:13:43
description: Spring in Action Ver. 4
---

# 3. 高级装配


- Spring profile

- 条件化 Bean 声明式

- 自动装配

- Bean 作用域

- Spring 表达式语言

## 3.1 Spring profile

```java
@Configuration
public class DataSourceConfig {

    @Bean(destroyMethod="shutdown")
    @Profile("dev")
    public DataSource embeddedDataSource() {
        return new EmbeddedDatabaseBuilder()
            .setType(EmbeddedDataabaseType.H2)
            .addScript("classpath:schema.sql")
            .addScript("classpath:test-data.sql")
            .build();
    }

    @Bean
    @Profile("prod")
    public DataSource jndiDataSource() {
        JndiObjectFactoryBean jndiObjectFactoryBean = new JndiObjectFactoryBean();
        jndiObjectFactoryBean.setJndiName("jdbc/myDS");
        jndiObjectFactoryBean.setResourceRef(true);
        jndiObjectFactoryBean.setProxyInterface(javax.sql.DataSource.class);
        return (DataSource) jndiObjectFactoryBean.getObject();
    }
}

```

不指定 profile 的 bean始终都会被创建

激活 profile 依赖 `spring.profiles.active` 和 `spring.profiles.default` 属性

有 active 的就用 active，没有的话用 default，两个都没有的话就没有激活的 profile

设置方式：

DispatherServlet 的初始化参数

Web 应用的上下文参数

JNDI 条目

环境变量

JVM 系统属性

int 测试类上用 @ActiveProfiles 注解

## 3.2 条件配置 Bean

```java
@Bean
@Conditional(MagicExistsCondition.class)
public MagicBean magicBean() {
    return new MagicBean();
}
```

```java
public class MagicExistsCondition implements Condition {
    public boolean matches(ConditionContext context, AnnotatedTypeMetadata metadata) {
        Environment env = context.getEnvironment();
        return env.containsProperty("magic");
    }
}
```

## 3.3 自动装配的歧义性

如果同时存在多个 Bean 匹配结果的话自动装配失效, NoUniqueBeanDefinitionException

```java
@Autowired
public void setDessert(Dessert dessert) {
    this.dessert = dessert;
}
```

```java
@Component
public class Cake implements Dessert { ... }

@Component
public class Cookies implements Dessert { ... }

@Component
public class IceCream implements Dessert { ... }

```
解决方式：primary bean， qualifier bean

```java
@Component
@Primary
public class IceCream implements Dessert { ... }
```
primary 只能同时存在一个

```java
@Autowired
@Qualifier("iceCream")
public void setDessert(Dessert dessert) {
    this.dessert = dessert
}
```

限定符必须和要注入的 bean 名称紧耦合

所有使用 @Component 声明的类都会创建为 Bean，并且 Bean ID 首字母变为小写的类名

@Qualifier 也可以和 @Component 组合使用，自定义限定符

也可以创建自定义注解

```java

@Target({ElementType.CONSTRUCTOR, ElementType.FIELD, ElementType.METHOD, ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Qualifier
public @interface Cold { }
```


## 3.4 Bean 作用域

默认情况下 bean 是作为单例创建的，不管注入多少次都是同一个实例

如果类里面会保持某些状态，单例重用会比较麻烦，容易污染对象

作用域：

- 单例 Singleton

- 原型 Prototype 每次注入或者通过 AC 获取的时候都会创建一个新的示例

- 会话 Session

- 请求 Request

```java
@Bean
@Scope(ConfigurableBeanFactory.SCOPE_PROTOTYPE)
public class Notepad { ... }
```

## 3.5 运行时值注入

属性占位符 Property Placeholder

SpEL 

```java
@Configuration
@PropertySource("classpath:/com/soundsystem/app.properties")
public class ExpressiveConfig {

    @Autowired
    Environment env;

    @Bean
    public BlankDisc disc() {
        return new BlankDisc(
            env.getProperty("disc.title"),
            env.getProperty("disc.artist")
        )
    }
}

```

getProperty 还可以用来在所需属性不存在的时候指定默认值

如果需要属性一定存在的话可以用 getRequiredProperty

```
String getProperty(String key, String defaultValue)

T getProperty(String key, Class<T> type, T defaultValue)
```
