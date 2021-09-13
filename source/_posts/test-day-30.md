---
title: test-day-30
categories: test
tags: test
description: 确实不熟悉 sed 和 grep
show: true
date: 2021-09-13 11:40:52
---

卡了一下午的字符串匹配

后来用 grep 和 sed 配合正则写出了魔法一样的语句

```bash
    old_imagetag=$(cat ${tableFile} | grep -o "${component}:[^ \|]*" | tail -1)
    sed -i "s/${old_imagetag}/~~${old_imagetag}~~ |\n| | ${imagetag} /g" ${tableFile}
```

grep -o 可以只选中匹配到的字符串，而不是包含它的一整行，only 的意思

`${component}:[^ \|]*` 正则，开头是component变量的值加上一个冒号，结尾是空格加上一个`|`，`\`用来转义，`*` 选中中间的任意字符

tail -1 可以用来选到最后一个匹配项

sed -i 可以对同一个文件原地替换，in place 的意思

s/ 表示 substitute，替换

这就里就是把 old_imagetage 加上 strikethrough， 然后补上 `|` 标识表格里当前行的结尾，`\n` 换行，

新的一行 `| | ${imagetag}` 这里是第一列空，第二列是 imagetag 

结尾不写 `|` 的理由是在替换的时候没有涉及到原本那一行的结尾标识，可以继续沿用