---
title: test-day-101
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-01-13 17:11:36
---
## Today's Task
- [ ] [ASAP] Property Page
- [ ] Migrate ReleaseMe from CRA to Vite
    - [x] Transfered config files
    - [x] Mock up Node builtin modules
    - [x] npm start

## Additional Task 
- [x] Rebuild image for Shadowbroker
- [x] Fix email sending on Node B
- [x] Release image for Nexus and initialize regresion

## Thought

### 1

Migrate CRA to Vite

#### 1 Update package.json

```json
"scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview"
  },
```

delete `react-scripts` from dependencies

install several vite devDependencies

```bash
npm i vite @vitejs/plugin-react vite-plugin-svgr
```

#### 2 Add Vite Config

`vite.config.ts`

```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import svgrPlugin from 'vite-plugin-svgr'
// import reactJsx from 'vite-react-jsx'

export default defineConfig({
    build: {
        outDir: 'build',
    },
    plugins: [react(),
        svgrPlugin({
        svgrOptions: {
            icon: true
        }
    })]
})
```

### 3. Update tsconfig.json

```json
{
  "compilerOptions": {
    "target": "ESNext",
    "useDefineForClassFields": true,
    "lib": ["DOM", "DOM.Iterable", "ESNext"],
    "allowJs": false,
    "skipLibCheck": false,
    "esModuleInterop": false,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "module": "ESNext",
    "moduleResolution": "Node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx"
  },
  "include": ["./src"]
}

```

then `npm i` or `yarn`

#### 4. Move index.html out

move `/public/index.html` to the root of the project

Remove `%PUBLIC_URL%`

Add script

```html
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
    <script type="module" src="/src/index.tsx"></script>
</body>
```

#### 5. Update ENV vars

search and replace all `process.env.REACT_APP_` to `import.meta.env.VITE_`
