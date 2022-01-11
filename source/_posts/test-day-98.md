---
title: test-day-98
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-01-10 10:04:41
---
## Today's Task
- [x] [urgent] Upload db.data onto artifactory
- [ ] [ASAP] Comment time
- [ ] [ASAP] Property page


## Additional Task 
- [x] Track Nexus-ui regression low passrate
- [x] Rebuild image for customizedlog.
- [x] Send Test Failure Email

## Thought

### 1

突然发现一整天不看手机也是一件需要挑战的事情了

我  不  对  劲

要踏踏实实去做事情才行

试了很多花哨的解决方案

种树，秒表，番茄钟……

最有效的还是直接丢进包里，眼不见为净

### 2

Target: deploy db.data's binary onto ATF

those jar files after mvn clean install?

liquibase.data uploads them without UploadBinary Job

这是在哪里触发的 upload to artifactory？？

maven deploy 的时候做的

所以看了一整个上午，答案已经呼之欲出了吧

release_job.sh 里面会根据当前 product 去找到对应的目录进去 mvn -e -q clean deploy 一把

在 pom.xml 里面设置一下 `<distributionManagement>`，脚本里加上判断，执行一下命令就 ok 了

```xml

<distributionManagement>
  <repository>
    <id>internal.repo</id>
    <name>Internal Repo Name</name>
    <url>Host to Company Repository</url>
  </repository>
</distributionManagement>

```

### 3

终究还是在一个只有两个页面的项目里加入了 React Router （霰弹枪警告

### 4

还是要用 Jira 去追踪自己的 Task

这样自己博客上的 daily task，就真的可以是认真打算今天做的事情，

进一步细化以后更容易执行

也就更不容易去咕咕咕

### 5

回想起了 10 年晚上在世博轴上奔跑的感觉

那时觉得身边的一切都如此新奇

半梦半醒间又想起了更早的感觉

08年的夏天，阁楼亭子间

CRT，时之笛


