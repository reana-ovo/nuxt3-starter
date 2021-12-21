## 安装 nuxt 3

```sh
npx nuxi init nuxt3-starter
cd nuxt3-starter
yarn install
yarn build
```



## 初始化 Commitizen

```sh
git init
yarn global add commitizen
commitizen init cz-conventional-changelog --yarn --dev --exact
```



## 添加 Eslint 支持

```sh
yarn add -D eslint @nuxtjs/eslint-config-typescript
```



## 添加 Prettier 支持

```sh
yarn add -D prettier eslint-config-prettier eslint-plugin-prettier
```



## 配置 Eslint

`.eslintrc` :

```json
{
  "plugins": ["prettier"],
  "extends": ["@nuxtjs/eslint-config-typescript", "standard", "prettier"],
  "rules": {},
  "overrides": [
    {
      "files": ["./pages/**", "./layouts/**"],
      "rules": {
        "vue/multi-word-component-names": "off"
      }
    }
  ]
}
```



## 配置 Prettier

`.prettierrc` :

```json
{
  "semi": false,
  "singleQuote": true,
  "TrailingComma": "all",
  "bracketSpacing": true,
  "arrowParens": "avoid"
}
```



## 添加 Tailwindcss 支持

```sh
yarn add -D tailwindcss postcss autoprefixer
yarn tailwindcss init
```



`tailwind.config.js` :

```js
module.exports = {
  content: [
    "./components/**/*.{js,vue,ts}",
    "./layouts/**/*.vue",
    "./pages/**/*.vue",
    "./plugins/**/*.{js,ts}",
    "./nuxt.config.{js,ts}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```



`postcss.config.js` :

```js
module.exports = {
    plugins: {
        tailwindcss: {},
        autoprefixer: {},
    },
}
```



`nuxt.config.ts`

```typescript
import { defineNuxtConfig } from 'nuxt3'

// https://v3.nuxtjs.org/docs/directory-structure/nuxt.config
export default defineNuxtConfig({
    typescript: {
        strict: true,
    },
    build: {
        postcss: {
            postcssOptions: {
                plugins: {
                    tailwindcss: {},
                    autoprefixer: {},
                },
            },
        },
    },
})
```



`assets/css/tailwind.css` :

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```



`App.vue` :

```vue
<script lang="ts" setup>
import './assets/css/tailwind.css'
</script>

<template>
  ...
</template>
```



## 添加 Stylus 支持

```sh
yarn add -D stylus
```



## 添加 Script

```json
// ...
  "scripts": {
    // ...
    "lint": "eslint --fix --ext .vue,.ts,.tsx,.js,.mjs .",
    "type-check": "npx vue-tsc --noEmit",
    "commit": "yarn type-check && yarn lint && git add . && git cz"
  },
// ...
```



## VSCode 扩展

`一些推荐的扩展` :

```
aaron-bond.better-comments
antfu.browse-lite
antfu.vite
antfu.where-am-i
bradlc.vscode-tailwindcss
csstools.postcss
DavidAnson.vscode-markdownlint
dbaeumer.vscode-eslint
esbenp.prettier-vscode
hollowtree.vue-snippets
jcbuisson.vue
johnsoncodehk.volar
johnsoncodehk.vscode-typescript-vue-plugin
MS-CEINTL.vscode-language-pack-zh-hans
octref.vetur
steoates.autoimport
streetsidesoftware.code-spell-checker
sysoev.language-stylus
TabNine.tabnine-vscode
vivaxy.vscode-conventional-commits
xyz.local-history
```

