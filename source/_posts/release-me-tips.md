---
title: release-me-tips
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-11-10 17:47:35
---
# 在配置 releaseme 跑起来的时候遇到的坑

## frontend

### 1. TS2339

```
$ npm run build

> release_me@0.1.0 build
> node prebuild.js && react-scripts build

Creating an optimized production build...
Failed to compile.

C:/Users/yunhaoliu/Projects/releaseme/frontend/src/Model/BackendMapper.ts
TypeScript error in C:/Users/yunhaoliu/Projects/releaseme/frontend/src/Model/BackendMapper.ts(20,55):
Property 'releaseme' does not exist on type 'string'.  TS2339

    18 |         "Firstpartynucleus": "FirstPartyNucleus"
    19 |     }
  > 20 |     static originDeployMapper: DeployMapper = backend.releaseme.flow.deployMapper as DeployMapper
       |                                                       ^
    21 |     static imageKeyTranslation: Record<string, string> = {};
    22 |     static Component: Record<string, string> = {};
    23 |
```
复制一份 Backend 里的 Application.yml 到 Frontend 里覆盖

如果开了 win10 的 Developer Mode,

git win 会在 Clone 的时候把软连接变成 Symbol link

如果不在就摆烂

### 2. localhost 启动

猛击 F12，Application -> Storage -> Local Storage 里面有个 token

Chrome 的快捷方式里，加上 `--disable-web-security`

开个新的窗口，在转圈圈的时候眼疾手快，猛击 STOP

F12, 同样的位置加入自己的 Token

### 3. localhost 直接启动了 PROD

本地 npm run build 了前端

后端的部分部署在了 linux 上

直接 serve -s build 的话，直接打开了 PROD

在相同域名下不同端口，依然会触发跨域

真正需要做的事情是，

要在 `src/Model/Request.tsx` 里加上 endpoint，是 `application.yml` 的后缀

```typescript
static endpoints: Record<string, string> = {
    "development": "https://releaseme.citools.ea.com",
    "local":       "http://local-releaseme.citools.ea.com:8080",
    "lyh":       "http://localhost:8080",
    "alpha":       "http://alpha-releaseme.citools.ea.com",
    "production":  "https://releaseme.citools.ea.com"
};
```

还有 `App.js` 里去掉 token 为空时的判断

```typescript 
render() {
    // if (Request.token)
    //     return <MainPage />
    // else
    //     return <RedirectPage />
    return <MainPage />
}
```

## backend

### 1. ENC 的密码设定

必须指定 `-DJASYPT_ENCRYPTOR_PASSWORD`, application.yml 里所有的 ENC 都必须 match

本地测的时候就不要这么麻烦了，直接在自己的 yml 里写明文

另外，密码给个简单的就好，别给自己找麻烦

### 2. application.yml 

同一个目录下，`application-xxx.yml` 里面的内容会覆盖 application.yml 的

需要指定 ENV_NAME

里面 localhost ，想要在其他机器上跑的话就需要替换成它的 ip

### 3. mysql docker

VM 分的磁盘太小了，docker 起不来

检查 log 就能知道原因

虚拟机，是存在极限的

所以我不用虚拟机了！！！

捡了台退役服务器装了 linux

ssh上去简单弄了下 docker

### 4. insert dummy data

测试用的假数据不知道怎么插进去…

它用了 webhook 去探 gitlab 上的新改动

而且 label 是一定要包含 releaseme 的

component 也必须要在列表里

直接往数据库里插表是不行的

