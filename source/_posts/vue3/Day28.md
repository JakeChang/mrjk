---
title: Vue3 從零開始學¹ - Day28 - Route
date: 2023-09-28 09:38:54
tags:
---
網頁最重要的就是換頁，俗稱路由，在 Vue3 要完成路由功能，必須要使用 route 。由於專案是使用 CLI 工具所產生的，所以這邊也必須要使用 CLI 工具來產生 route 的功能。

開啟終端機，輸入以下指令，安裝 route 的功能：

```bash
vue add router@next
```

然後接著會詢問是否使用 history mode：

```bash
? Use history mode for router? (Requires proper server setup for index fallback in production)
```

完成之後，CLI 工具會自動完成產生具有 route 功能的專案，所以這個時候重新開啟專案，會發現程式碼跟之前有異同。

這邊就一個一個來看是如何產生 route 功能的。

### Route

先來看看 route/index.js 這個檔案：

```javascript
import { createRouter, createWebHistory } from 'vue-router'
import HomeView from '../views/HomeView.vue'

const routes = [
  {
    path: '/',
    name: 'home',
    component: HomeView
  },
  {
    path: '/about',
    name: 'about',
    // route level code-splitting
    // this generates a separate chunk (about.[hash].js) for this route
    // which is lazy-loaded when the route is visited.
    component: () => import(/* webpackChunkName: "about" */ '../views/AboutView.vue')
  }
]

const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes
})

export default router
```

這邊會使用一個陣列 routes 來儲存需要跳轉的頁面，例如：

```javascript
{
  path: '/',
  name: 'home',
  component: HomeView
},
```

這就表示當網址路徑指向 http://localhost:8080/ 時，會使用 HomeView 這個 .vue 檔案。

又例如：

```javascript
{
    path: '/about',
    name: 'about',
    // route level code-splitting
    // this generates a separate chunk (about.[hash].js) for this route
    // which is lazy-loaded when the route is visited.
    component: () => import(/* webpackChunkName: "about" */ '../views/AboutView.vue')
  }
```

這就表示當網址路徑指向 http://localhost:8080/about 時，會使用 AboutView 這個 .vue 檔案。

最後使用 `createRouter`，設定 history 為 createWebHistory，這裡就表示使用 HTML5 的 History API 來產生路由的功能，並且傳入 routes 陣列：

```javascript
const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes
})
```

最後，這個 route/index.js 檔案的程式碼可以精簡成：

```javascript
import { createRouter, createWebHistory } from 'vue-router'

const routes = [
  {
    path: '/',
    name: 'home',
    component: () => import('../views/HomeView.vue')
  },
  {
    path: '/about',
    name: 'about',
    component: () => import('../views/AboutView.vue')
  }
]

const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes
})

export default router
```

### App.vue

回到 App.vue 這個檔案：

```html
<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/>
</template>
```

這邊就非常簡單，如果已經使用 route/index.js，就必須指定 `<router-view/>` 來開啟。

然後使用 `<router-link to=""></router-link>` 進行路徑連結。

指定 `<router-link to="/">Home</router-link>` 就表示跳轉到 HomeView.vue。

指定 `<router-link to="/about">About</router-link>` 就表示跳轉到 AboutView.vue。

[今日程式碼範例](https://stackblitz.com/edit/vue-hbd7ej?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day28 [完]**
