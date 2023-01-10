---
title: JS 笔记 第 2 章 HTML中的JavaScript
categories: 读书笔记
tags: JavaScript
description: 有关script元素的使用小知识，包括加载顺序和异步脚本使用注意事项等
show: true
date: 2021-08-08 00:41:46
---

# \<script>元素

在行内使用JavaScript的时候，字符串 \</script> 不被允许出现，会被浏览器当成script结束，需要使用转义字符

包括我在用md写这篇文章的时候，如果不加转义字符，前文内容也会被浏览器当成script结束

使用了src属性的\<script>元素不应该再在里面包含其他JavaScript代码。

浏览器只会下载执行外部的脚本文件，忽略行内代码

src属性可以是一个来自外部域的完整url，浏览器会发get请求到目标地址

所有script元素会依照在网页中出现的次序被解释，不用defer或async的时候，会严格按照出现次序

现代通常把\<script>放在\<body>元素中的页面内容后面，这样就会先渲染完所有页面内容以后再处理js代码

异步脚本可以不必等待其他脚本，也不阻塞文档渲染，并不能保证执行次序

异步脚本不应该在加载期间修改DOM，只适用于外部脚本

动态加载脚本

```js

    let script = document.createElement('script');
    script.src = 'xxx.js';
    script.async = false; // 默认是异步，手动设置为同步加载即可统一加载行为
    document.head.appendChild(script);

```
显式声明以让预加载器知悉动态请求文件存在

```html

    <link rel="preload" href="xxx.js">

```

通过 \<nonscript> 可以指定浏览器在不支持脚本的时候显示的内容
