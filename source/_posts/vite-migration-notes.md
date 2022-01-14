---
title: vite-migration-notes
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-01-13 17:26:48
---

# 1 Safe-Buffer Undefined
```
index.js:12 Uncaught TypeError: Cannot read properties of undefined (reading 'from')
    at node_modules/safe-buffer/index.js (index.js:12:12)
```

```
npm i buffer
```

# 2. util.inherits is not a function
```
Uncaught TypeError: util.inherits is not a function
    at node_modules/jws/lib/data-stream.js (data-stream.js:39:6)
```

util is a node builtin module and isn't/won't get polyfilled by vite
you will need to add polyfills for node builtins

```
npm i util
npm i inherits-browser
```

```
Uncaught TypeError: Object prototype may only be an Object or null: undefined
    at Function.create (<anonymous>)
    at Object.inherits (inherits_browser.js:6:31)
    at node_modules/jws/lib/data-stream.js (data-stream.js:39:6)
```

do several mock ups in `vite.config.ts`

```typescript
    define:{
      'process.env': process.env,
    },resolve: {
        alias: {
            inherits: './inherits.js',
        }
    }
```

and then create `./inherits.js`

```javascript
function inherits(ctor, superCtor) {
    if (!superCtor.prototype) return
    ctor.super_ = superCtor
    ctor.prototype = Object.create(superCtor.prototype, {
        constructor: {
            value: ctor,
            enumerable: false,
            writable: true,
            configurable: true,
        },
    })
}
module.exports = inherits
```

# 3. crypto has been externalized for browser compatibility

```
Uncaught (in promise) Error: Module "crypto" has been externalized for browser compatibility and cannot be accessed in client code.
    at Object.get (__vite-browser-external:crypto:3:11)
    at Function.jumpToOKTA (Jwt.ts:49:42)
    at App.componentDidMount (App.tsx:20:17)
```

# 4. react-router & vite ts error


```
node_modules/react-router/index.d.ts:151:74 - error TS1110: Type expected.

node_modules/vite/types/customEvent.d.ts:2:60 - error TS1110: Type expected.
```

Upgraded Typescript from `3.9` to the latest `4.5.4`

# 5. TS2794

```
src/Components/Layout/FlowPlayground.tsx:75:101 - error TS2794: Expected 1 arguments, but got 0. Did you forget to include 'void' in your type argument to 'Promise'?

75         await new Promise((resolve, _) => filter.setState({ statusFilter: FlowStatus.Focus }, () => resolve()));
```


# 6. TS2571

```
src/Model/Requests.tsx:130:33 - error TS2571: Object is of type 'unknown'.

130             let promise = await ex.json();
```


in `tsconfig.json`, set `useUnknownInCatchVariables` to `false`


# 7. Could not resolve './lib/sign-{}' from ./lib/sign-{}?commonjs-external

```
Could not resolve './lib/sign-{}' from ./lib/sign-{}?commonjs-external
error during build:
Error: Could not resolve './lib/sign-{}' from ./lib/sign-{}?commonjs-external
    at error (C:\Users\yunhaoliu\Projects\releaseme\frontend\node_modules\rollup\dist\shared\rollup.js:158:30)
    at ModuleLoader.handleResolveId (C:\Users\yunhaoliu\Projects\releaseme\frontend\node_modules\rollup\dist\shared\rollup.js:22384:24)
    at C:\Users\yunhaoliu\Projects\releaseme\frontend\node_modules\rollup\dist\shared\rollup.js:22363:26
[!] Error: unfinished hook action(s) on exit:
(vite:load-fallback) load "C:/Users/yunhaoliu/Projects/releaseme/frontend/node_modules/antd/node_modules/rc-tree-select/es/utils/strategyUtil.js"
```

remove `stream: {}, global: {}, process: {}` in `vite.config.ts` which seemed to be mock ups of node builtin modules

# 8. Module is not defined

```
Uncaught ReferenceError: module is not defined
    <anonymous> http://local-releaseme.citools.ea.com:8080/assets/vendor.9c99dfbb.js:169
```

没啥办法了 换包吧

JWT，Crypto，