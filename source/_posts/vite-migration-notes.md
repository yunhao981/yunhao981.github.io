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
        stream: {},
        global: {},
        process: {}
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