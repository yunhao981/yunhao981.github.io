---
title: test-day-72
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-11-22 10:14:58
---
## Today's Task
- [ ] change image tag pattern
- [ ] onebox vmip 
    - [x] get client ip
    - [x] get hostname
    - [ ] get server ip
    - [ ] get vm ip
    - [x] no need to get ips from frontend
    - [ ] use nginx or httpd instead of node
- [ ] Transfer jenkins jobs
    - [x] use web hub
    - [x] check CP Docker status
    - [x] Fix Post Steps
    - [x] Fix QAV5-INTBVT
    - [ ] Porpoise_Docker ssh permission
- [x] check audit / merge output exception
    - [x] Code-Merge
    - [x] Component Audit
    - [x] Component Audit V4

## Additional Task 
- [x] Fix FlowCard Rerun button after review

## Code Review

不要这么写:

```typescript
checkRerunStatus(flow: Flow) {
    this.currentFlowCanRerun(this.props.flow).then(isAllowedRerun => {
        this.setState({
            isAllowedRerun: isAllowedRerun
        })
    });
    this.currentFlowNotRerunReason(this.props.flow).then(erason => {
        this.setState({
            reasonNotRerun: reason
        })
    });
}
```

用 async 啊魂淡

```typescript
async checkRerunStatus(flow: Flow){
    let isAllowedRerun = await this.currentFlowCanRerun(this.props.flow);
    let reason = await this.currentFlowNotRerunReason(this.props.flow);
    this.setState({
        isAllowedRerun: isAllowedRerun,
        reasonNotRerun: reason
    })
}
```

这样写明显就清楚多了


## Thoughts

昨晚和蚊子亲密到凌晨四点半

内心深处的焦躁苦闷与不安如出一辙

为了避免自己再度陷入高三的逃学循环

想了想还是披上衣服出了门

脑海里已经在循环 Take Five 了

中午从 11 点睡到了 1 点多

梦里也在趴着做梦

可能是姿势造成了缺氧吧

醒来手麻了好几回

试着坐直了调整

只是抵挡不住睡意来袭

梦见我需要猛击 F5 才能醒过来

但键盘按键越来越少，只到 F4 为止

是处在趴在桌上动不了的状态

停电，所有灯全灭

巧克力饼干，很好吃