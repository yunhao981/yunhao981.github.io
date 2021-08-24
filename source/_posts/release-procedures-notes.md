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
| PlayerInfractionLedger     | Guardiola    | 瓜帅？ |
| PlayerOwnership            | Shadowbroker | |
| PlayerControl              | Porpoise     | |
| PlayerSettings             | ibex         | |
| SubscriptionRewards        | hyas         | |
| Healthy-play-*             | saola        | |



# paragon 相关

在每次 release paragon 的时候，需要手动检查 git log

1. 在 nucleus 下，git fetch 当前release分支
2. git log，确认commit id是否包含当前 CHG 分支的内容
```bash
git log liquibase.data/src/main/resources/changelogs/paragon/
```
3. 如果有变动更新，通知 Yanqin 或 Guangyao

# Code Merge 相关

如果遇到了权限问题， `/home/${user}/code_merge/${repo}` 下执行 `git remote -v` 确认 url 的 token 是否配置正常

如果不正常，

```bash
sudo git remote set-url origin https://svc_candi_git_admin%40ea.com:xuDCuBjVKLSGT_XCestx@gitlab.ea.com/eci/${repo}.git
```


# release image 相关

在 Release${repo} 执行完毕后，通常结尾会给出一个自动跳转至 upload binary 的 job

需要确认这个 job 是否执行成功，否则将不会有更新推送至 Artifactory

# STG 细节

先铺 nexus 再铺 nucleus 可以节省时间

并不能在铺完 STG 之后立马执行 Sanity Check，需要延迟 2 分钟左右，等待 service 完全启动

# Recut 相关

Wiki page上的原有 image 记录需要用删除线划掉，并且删掉 review 标签

版本号会从 CHGxxx 变为 CHGxxx_1st_cut

# Regression 注意事项

先要检查 Sanity 对应组件的部分 Job 是否 Success，确认铺 STG 是否完成

设置 code client for rerun，减少出错反复运行调试的准备工作时间开销

发起人的邮件填公用自动账号 EADPAutoExReportingS@ea.com

至少开 2 台 VM，可以作为一台出玄学故障的备份，通常会根据 Component 的数量和种类开 4 台

选择 Component 的时候要注意名字结尾是否标注了 Int，Int 仅用于 CHGxxx-INT 分支

shadowbroker 单独跑

risk, risk-ui 单独运行

nexus, nexus-ui 单独运行

在 cut 当日，下午一点前发起 regression
