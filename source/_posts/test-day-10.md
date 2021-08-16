---
title: test-day-10
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-08-16 15:11:37
---
坐地铁的时候迷迷糊糊眯了一会，双手交叉握着手机

所以今天右手手腕中心会有点酸痛，有点轻微的腕管综合征迹象

今天修改好了 Nucleus.solr.exporter 的 image tag pattern

和 solr 的几乎一摸一样，但因为修改的分支太旧了，落下了 120 个 commit

所以发生了 merge conflict, 因此需要 rebase

在这上面花了很多时间，所以单独开了篇笔记记录，但以后再碰到类似的事情，就有头绪解决了

另外学到了一个非常酷炫的 bash 脚本写法

```bash
    [ ! -z $3 ] && chgNumber=$3 || chgNumber="CHGNULL"
```

判断第三个参数是否为空，若不为空，则将其赋值给 chgNumber

若为空，则将 "CHGNULL" 赋值给 chgNumber

另外更新了Fastrun Daily Tracking

对于各类错误发生的原因，还需要多调查

关于 fast-liquibase pipeline 的修复，还是有点棘手的，没有额外的什么思路

探索了一下 Aritifactory 的 release 部分，通过观察这个 pipeline 出错的参数，可以发现并不是所有的 Repo 其 build image version 都在 Artifactory 上有对应的文件夹，那自然是会报 404 的

修复的思路那就是把它们给补上，但不清楚具体的细节，也要再多问问

临时先写了个判断 tarfile 是否存在，若不存在则 exit 1

至少在 wget 没有成功从 Artifactory 处获得 tarfile 的时候，最后不会报个 success 了吧