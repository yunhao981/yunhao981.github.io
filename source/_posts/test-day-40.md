---
title: test-day-40
categories: test
tags: test
description: react 小坑：setState 同步异步？
show: true
date: 2021-09-29 17:15:39
---
早上的 cut build 还算是比较顺利的

keymaster local regression 跑不过，

是 Guardiola 的配置没有更新导致的，需要手动指定 release branch

重跑得到的结果和 CHG0150430 的一样

onebox setup page 里搞定了同步更新 state

```js

constructor(props) {
    super(props)
    this.state = {
        build: true
    }
}

handleCheckChange = e => {
    this.setState({
        build: !this.state.build
    })
    console.log(this.state.build)
}
```

这样得到的结果依然是 true

需要给 setState 一个回调函数

```js
handleCheckChange = e => {
    this.setState(state => {
        return {build: !state.build}
    }, ()=>console.log(this.state.build))
}
```

第一个参数是更新 state 前（也就是当前）的状态

第二个参数是回调函数，这里面的 state 才是更新后的状态