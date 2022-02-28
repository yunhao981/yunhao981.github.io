---
title: test-day-128
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-02-28 10:37:57
---
## Today's Task

## Additional Task 

## Thought

### 1

```
[Warning] One or more build-args [env] were not consumed
```
ARG 在跑完 Dockerfile 就会消失

ENV 不会

这里 docker build --build-arg env=cn 的时候不知为啥就是传不进去

有可能是跨 stage 的时候 env 就不通用了？不太确定

后来直接拆成两个 dockerfile 绕开了

### 2

container run 起来瞬间 exit

Docker Exited 127

然后看了下 log，发现是启动 nginx 的脚本没有 COPY 过来

docker logs -t onebox.setup.cn

2022-02-28T07:43:04.208781427Z /bin/sh: 1: ./startup.sh: not found

...后来还忘记改权限了

### 3

nginx 到底用的哪个端口……

周五看是 5000

现在起来以后里面又变成了默认的 80

full-cycle script 里面 run 的时候是 -p 80:5000, 外面 host 80，里面是 5000

所以直接给一份 nginx.conf 指定下端口吧

### 4

指定了端口之后为什么会去找 `/etc/nginx/html` ？？？


