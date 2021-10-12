---
title: release-procedures-notes
categories: test
tags: test
description: 人工执行整个 release cut build 流程中的注意事项
show: true
date: 2021-08-24 18:06:24
---
# 命名改动对应表

| Current Name               | Old Name     | Comment |
| -------------------------- | ------------ | ------- |
| FirstPartyOfferEntitlement | Kanas        | 喀纳斯湖？|
| FirstPartyCheckout         | Venice       | 威尼斯商人？ |
| PlayerSearch               | Chihiro      | 千寻找父母？ |
| CommerceProvision          | Paragon      | 新加坡商场？ |
| ValueTransfer              | Citadel      | |
| PlayerInfractionLedger     | Guardiola    | 瓜迪奥拉做假账？ |
| PlayerOwnership            | Shadowbroker | |
| PlayerControl              | Porpoise     | |
| PlayerSettings             | ibex         | |
| SubscriptionRewards        | hyas         | |
| Healthy-play-*             | saola        | |


# checklist

曾经有过，人工熟练后逐渐失去效用

为了避免遗漏 component，在自动化搞定之前

还是开了个 Excel

后来真的发现不好用

# paragon 相关

在每次 release paragon 的时候，需要手动检查 git log

1. 在 nucleus 下，git fetch 当前release分支
2. git log，确认commit id是否包含当前 CHG 分支的内容
```bash
git log liquibase.data/src/main/resources/changelogs/paragon/
```
3. 如果有变动更新，通知 Yanqin 或 Guangyao

# Audit Tool & Component Audit

每次默认一定要有的 nucleus, nexus, paragon

DOUBLE CHECK 不要漏 component

Keymaster 和 Access 需要手动检查 

Keymaster 用 releases/rel550

Access 用 releases/rel551

Saola 的 Saola.infra 下，存在其依赖组件，需要用各自单独的 Pipeline 去 build image，比如说 Kafka，Cassandra, Zookeeper

# Code Merge 相关

如果遇到了权限问题， `/home/${user}/code_merge/${repo}` 下执行 `git remote -v` 确认 url 的 token 是否配置正常

如果不正常，换成带有 secret_token 的 link

如果还是遇到了权限问题，而且gitlab 的账号配置没问题的话，再重新设置一次一模一样的 url 

```bash
sudo git remote set-url origin https://svc_candi_git_admin%40ea.com:${token}@gitlab.ea.com/eci/${repo}.git
```

如果 merge conflict，通知完 Yanqin / James / Kyle 之后问 Owner

然后登上 testinfra-master 进 /home/root/code-merge/ 里面找到对应 repo

git status 确认哪个冲突了，没有的话手动 merge 一把

改完之后 add, commit, push 一条龙

最后一定一定要去再执行一次 code-merge pipeline，

目的是为了删掉 CHG branch，同时保证真的所有改动都合并进 release 了

# release image 相关

在 Release${repo} 执行完毕后，通常结尾会给出一个自动跳转至 upload binary 的 job

需要确认这个 job 是否执行成功，否则将不会有更新推送至 Artifactory

需要根据 commit 标识符人工确认 gitlab ，image 是否包含了目标对应的改动

如果邮件 / CM 里指定的 component 名字太模糊，需要去确认具体的内容

如果遇到了服务器磁盘容量不够，no space left 之类的情况，先问问 Jen 执行 docker prune

实在没啥办法又很紧急的话，发邮件问 24x7

# STG 细节

先铺 nexus 再铺 nucleus 可以节省时间

并不能在铺完 STG 之后立马执行 Sanity Check，需要延迟 2 分钟左右，等待 service 完全启动

# Recut 相关

Wiki page上的原有 image 记录需要用删除线划掉，并且删掉 review 标签

版本号会从 CHGxxx 变为 CHGxxx_1st_cut

# Regression 注意事项

先要检查 Sanity 对应组件的部分 Job 是否 Success，确认铺 STG 是否完成

nexus ui failed， use new test cases

```
com.ea.eadp.nexus.portal.tests.newconsole.TestScenarios_Console_AccountSelfRecovery#testDisabledAccountRecovery_trustworthy_NewEmail
```

设置 code client for rerun，减少出错反复运行调试的准备工作时间开销

发起人的邮件填公用自动账号 EADPAutoExReportingS@ea.com

至少开 2 台 VM，可以作为一台出玄学故障的备份，通常会根据 Component 的数量和种类开 4 台

晚上开的话可以冲到 8 台 10 台，因为是使用率低谷

选择 Component 的时候要注意名字结尾是否标注了 Int，Int 仅用于 CHGxxx-INT 分支

shadowbroker 单独跑

risk, risk-ui 单独运行

nexus, nexus-ui 单独运行

在 cut 当日，下午一点前发起 regression

确认 branch 设置，component list

# Int-Regression 注意事项

`(legacy) eaid-proxy-int` 仅在 INT 时加入

如下 Components 仅在 CD Regression 时加入
 - consoletracking
 - identity
 - infra
 - batch-framework

# Sign-off 相关

如果当前 production 中包含若干 INT

同一个 repo 在先前 A 版和 B 版里都有

那么 A 如果没签可以签掉

而如果这个 repo 在 C 版 里也有

但 C 不是当前 prod

那么 B 不能直接签

可以在 cm 里的详情找到其所属 production

也可以在 production 的 wiki page 里确认到
