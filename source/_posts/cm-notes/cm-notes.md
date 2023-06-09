---
title: CM-Notes
categories: Test Infra Manual
tags: Test Infra Manual
description: CM Full Process
show: true
date: 2023-05-25 13:10:18
---
## Audit

### release version wiki page

nucleus 一定要带上 Risk, 单独列出来

并且 risk & risk-ui 独立于其他 nucleus componet 单独跑 regression

nexus 一定要带上 Accounts.grpc

Citadel 和 Customizedlog 这两个即便没有 code change 也要一起跑 regression

有些 component 新的 commit 直接进了 release 分支，audit 探不到，需要 manual check

## Code Merge

上一个 CM 没签完的话下一个 CM 的 code 不能急着合进 release

如果需要 recut 上一个 CM 的话要保证不带进下一个 CM 的 commit

## Release

mvn BUILD FAILURE 找 dev 看

no space left 找 ops 清

docker build 看情况, push failure 找 ops

偶尔有 post step 里发 slack 消息发失败，不影响 image本身

Kanas 如果需要 manual release 就用 precise release kanas

## Deploy STG

更新 liquibase 以后再铺 STG

## Refresh Catalog DB

每次 CM 重刷 Promotion Rules

有些 nucleus test case 会去 call catalog，如果 promotion rules 堆积太多的话 catalog 回复就会慢导致 case 跑败

每月重做一次 DB，原因同上

## STG Sanity

## Regression

### Code Client for Rerun

fr-cn-a, cd /home/shdev/fastrun/signoff_client_tis

./test.sh 会去 pull 一次 source code

所以要在 merge 完之后去跑

```bash
mvn clean install -DskipTests -T 5 -Dmaven.repo.local=/home/shdev/fastrun/signoff_client_tis/repository/
```

有可能会跑不过，线程数要相应调整

机器上的 git 是远古版本1.8，没有 restore

### Sign off onebox

从 local regression 里找台 onebox, keep 99小时以上, 铺上所有当前 cm component

弄两三台，兼顾 FullCycle 和 HoroScope , 互为备份

签完之后记得释放

## Watcher Report

Watcher Report 下班前发一份出去，从已有结果里找一份最好的，如果晚上有更好的再发一次

挑没有 env issue的，passrate 99%+，公共账号发，账号 issue 找 it, env issue 找 dev / FR Admin

CN Watcher Report -> Local

CD Watcher Report -> STG

STG Watcher 在 CM Day 铺完 STG 全起来后，把 job 开出来跑

### Parameters for components

一般在 FR 上从上一个 CM 起的 regression 直接 rerun

LB Components 在 test-infra-node-b 上由 owner 单独跑

ops 铺完 int 以后起 int regression

不要漏掉 Component

## Sign off

Keymaster liquibase INT 邮件可以不用发, 从 Oracle 迁移到 MySQL 了

走 CICD 上 INT 的 component 在 PRD wiki 上时，要找 owner 单独确认能不能签

可以直接签掉: liquibase images 和 INT Regression 里面签完的 component

## Ops Deploying INT

如果有新的 component 要临时加，要在 wiki page 上标注出来，并且在 #ci-deployments 里说一声

ops 直接看 wiki page 是不知道哪些有更新的

## INT Regression

Risk & Risk UI 最多 1 台 1box 跑

无法 Rerun 单个 legacy component, 至少要带上 Association 一起跑

如果对结果没有信心，可以 recover result

## 踩到过的坑

Audit 缺 Component -> Manual check

起 regression 的时候忘记带上 Risk / Preferences Center / Value-Transfer / Customizedlog -> trigger 完 regression 对着 wiki 再确认

recut 更新页面的时候误删 image version -> 划删除线代替退格删除

公共账号邮箱登录失败 -> IT

Sign off client 炸了并且没有备份 -> 每次先起 local，跑完以后 keep 三台

image 没推到 AWS Repo -> nova-utility 上去推一把，推完及时修 build script

FR 上跑 local 的时候 HS 挂了 -> 及时反馈

## Reminders

base image 有更新的时候，需要从 IAD2 里移到 harbor 上

因为 ACL 的缘故，k3s-onebox 不通 Image Release Registry，需要在 Nova-Utility 上把 baseimage 推到 AWS-int Registry

再在 Test-Infra-Master 上把 baseimage 移到 Harbor 上

每个月 China Build Host 上重做 image 并 tag 到 latest
