---
title: slackbot-dev-notes
categories: slackbot
tags: slackbot ts js
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2023-01-05 16:05:14
---

## Convert JS to TS

```bash
npm install typescript ts-node
npx tsc --init
```

然后会有一份 tsconfig.json

大致是改了下面这些配置

把原本的源码扔进 ./src 里面

然后挨个调整下 function return type 和 parameter type

以及 import 和 export

```json
"target": "es2016",
"module": "commonjs",
"rootDir": "src",
"moduleResolustion": "node",
"resolveJsonModule": true,
"allowJs": true,
"checkJs": true,
"sourceMap": true,
"outDir": "dist",
"allowSyntheticDefaultImports": true,
"esModuleInterop": true,
"forceConsistentCasingInFileNames": true,
"strict": true,
"skipLibCheck": true
```

## config files

原本一大堆 token 是写在 json file 里的

用 `dotenv` 也许可以更优雅

```typescript
import { resolve } from 'path';
import { config } from 'dotenv';

const pathToConfig = '../../.env';
config({ path: resolve(__dirname, pathToConfig) });
```

```typescript
import './utils/env';

const foo = process.env.BAR;
```

## Docker

### 1

Q: image 1GB+

A: 用 `node:18-alpine`

### 2

如果是前端项目，也许可以 build static files 然后用 nginx host

## Call Jenkins with paramerters

### parameters form data

data: Map<String, String> or FormData, `Object.fromEntries(parameters)`

`headers: { Content-Type: multipart/form-data }`

### jenkins https support

```typescript
httpsAgent: new https.Agente({rejectUnauthorized: false})
```

### queue item 404 when postman testing

jenkins queue item id 只会保留半分钟左右，

queue item id -> build id -> build url

### 

```typescript
import crypto from 'crypto';
httpsAgent: new httpsAgent({
    secureOptions: crypto.constants.SSL_OP_LEGACY_SERVER_CONNECT
})
```

### FormData

FormData 从 node 16 以后开始支持，早了认不出


