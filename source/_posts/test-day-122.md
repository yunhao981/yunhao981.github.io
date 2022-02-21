---
title: test-day-122
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-02-18 10:24:35
---
## Today's Task
- [ ] Property Page
    - [ ] Fix Issues after review

## Additional Task 

## After work Task
- [ ] Deploy Cassandra in Docker on Linux

## Thought

### 1

竟有如此离谱

JB 的 Ktor Http Api 示例代码，在家跑能起来

但跑测试的表现是请求 8080 端口 404

同一份代码直接 clone 下来在办公室机器上就通了……

回去看看这个端口开了没，是不是被占用了

### 2

说起来经常会有 8080 被占用，但 idea 上跑着的所有项目都停掉了

```
netstat -ano | grep :8080
```

win 下可以用:
```
taskkill /PID ${PID of process using 8080} /F
```

## Code Review:

### 1. 为啥我老是喜欢用 forEach 捏

哦拜托这样真的超罗嗦的

forEach() 返回的是 undefined，map 至少会给个数组

所以这里在 forEach() 里面试图塞进数组的行为显得相当机车

而且这里 properties 永远不会 === null，它是初值个 {} ，而 {} != {} 且 {} !== {}

```typescript
renderOptions(properties: {[key: string]: string}) {
    let options: {value: string, label: JSX.Element}[] = [];
    if (properties !== null) {
        Object.keys(properties)?.forEach((key) => options.push(this.renderOptionItem(key, properties[key])))
    }
    return options;
}
```

Emmmm that looks better 

```typescript
renderOptions(properties: {[key: string]: string}) {
    return Object.keys(properties)?.map((key) => this.renderOptionItem(key, properties[key]));
}
```

### 2. map 到底返回了个啥？

```typescript
let tableItem: JSX.Element[] = [];
if (dataSource !== null) {
    Object.keys(dataSource)?.map( key => {
        tableItem.push(
            <tr key={key}>
                <td>{key}</td>
                <td>{dataSource[key]}</td>
            </tr>
        )
    })
}
```
map 本身返回的就是个数组，就不用再特地开个新的去存进去

```typescript
{
    Object.keys(dataSource)?.map( (key) => (
        <tr key={key}>
            <td>{key}</td>
            <td>{dataSource[key]}</td>
        </tr>
    ))
}
```

### 3. 展开运算符

```typescript
 renderOptions(properties: {[key: string]: string}) {
    let options: {value: string, label: JSX.Element}[] = [];
    if (properties) {
        Object.keys(properties)?.forEach((key) => options.push(this.renderItem(key, properties[key])))
    }
    return options;
}
```

```typescript
let history = { [property]: this.state.property };
let mergedHistory = { ...this.state.searchHistory, ...history }
this.setState( {searchHistory: mergedHistory});
```
