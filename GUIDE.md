## 安装 nuxt 3

```sh
npx nuxi init nuxt3-starter // replace `nuxt3-starter` with your app name
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
yarn add -D eslint @nuxtjs/eslint-config-typescript eslint-plugin-nuxt
```



## 添加 Prettier 支持

```sh
yarn add -D prettier eslint-config-prettier eslint-plugin-prettier
```



## 配置 Eslint

`.eslintrc` :

```json
{
  "env": {
  	"vue/setup-compiler-macros": true
  },
  "plugins": ["prettier"],
  "extends": [
    "@nuxtjs/eslint-config-typescript",
    "plugin:nuxt/recommended",
    "prettier"
  ],
  "rules": {
  	"vue/multi-word-component-names": "off"
  }
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



## 添加 Sass 支持

```sh
yarn add -D sass
```



## 添加类型检查

```sh
yarn add -D vue-tsc
```



## 添加 Script

```json
// ...
  "scripts": {
    // ...
    "lint": "eslint --fix --ext .vue,.ts,.tsx,.js,.mjs .",
    "type-check": "vue-tsc --noEmit",
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
github.copilot
hollowtree.vue-snippets
jcbuisson.vue
johnsoncodehk.volar
johnsoncodehk.vscode-typescript-vue-plugin
MS-CEINTL.vscode-language-pack-zh-hans
steoates.autoimport
streetsidesoftware.code-spell-checker
syler.sass-indented
TabNine.tabnine-vscode
vivaxy.vscode-conventional-commits
xyz.local-history
```

