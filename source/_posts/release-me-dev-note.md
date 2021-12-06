---
title: release-me-dev-note
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-11-30 14:30:13
---
# 在 ReleaseMe 上写 bug 的开发笔记

## 1. disable rerun button

PLACE_HOLDER

以后想起来再补上

翻页的时候，flow id 不会变

componentDidUpdate 里面 prev.props 和 this.props 变更的时候要精确到具体的某一个 props

不要用一长串连在一起的 `.then()` ，直接 `let foo = await bar();`

## 2. delete comments

CommentController, CommentInfoDao, CommenInfoMapper

CommpenInfoType, CommentInfoDB,

ResponseEntity

在 Mapper 里面写 SQL 的时候，DB 里面的列名、CommentInfoDB 类里的 Property name， 一定要各自对应上… 别写错了

虽然这几个类之间的关系完全搞不清楚

但还是照猫画虎撸出来了 DELETE comment api

Button 的 onChange 需要给的是 callback，而不是一个返回值类型为 void 的 function

在遍历 List Item 的时候，ANT List 的索引和 dataSource 好像可以在 callback 里直接拿到这个对象，但并不能直接 console.log 出来，但这个对象的属性好像是可以访问到的