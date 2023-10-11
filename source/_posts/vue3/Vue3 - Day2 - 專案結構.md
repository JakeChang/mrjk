---
title: Vue3 - Day2 - 專案結構
date: 2023-09-02 17:20:26
tags:
---

在上一個單元，已經學會了如何使用 Vue3 的 CLI 工具來建立專案，而在建立好專案之後，可以使用 Visual Studio Code 來打開 vue-demo 這個資料夾，在左側的目錄上可以瀏覽整個專案的結構：

![https://ithelp.ithome.com.tw/upload/images/20230902/20162607u0TQZmLXgk.png](https://ithelp.ithome.com.tw/upload/images/20230902/20162607u0TQZmLXgk.png)


總共會有這些資料夾檔案：

* node\_modules
* public
* src
* .gitignore
* babel.config.js
* jsconfig.json
* package-lock.json
* package.json
* README.md
* vue.config.js
    

先看 public 與 src 這兩個資料夾就好，其它的設定檔案可以先忽略不看，之後會再慢慢介紹。而 Vue3 的主程式流程，會先從 src/main.js 這個檔案開始：

```javascript
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')
```

程式邏輯很簡單，它會先引用 App.vue ，而 App.vue 就是一開始建立專案時，會自動產生好的頁面。經過 import 之後，呼叫 `createApp`，並且渲染(mount) 到 `#app` 之上，`#app` 可以把它當成一個變數。

`#app`  這個變數可以在 public/index.html 裡找到：

```xml
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <link rel="icon" href="<%= BASE_URL %>favicon.ico">
    <title><%= htmlWebpackPlugin.options.title %></title>
  </head>
  <body>
    <noscript>
      <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled. Please enable it to continue.</strong>
    </noscript>
    <div id="app"></div>
    <!-- built files will be auto injected -->
  </body>
</html>
```

在這一行 `<div id="app"></div>` 可以找到 `id="app"` 。

所以整個 Vue3 的程式邏輯的流程就是：

在 src/main.js 內引用 App.vue ，然後渲染到 public/index.html 。

接下來直接打開 App.vue，先不要理會裡面的程式結構，一開始看一定看不懂，只要先了解每個 .vue 檔案都有主要的標籤，分成三個部分：

```javascript
<template>
...
</template>

<script>
...
</script>

<style>
...
</style>
```

* template：相關 html 標籤語法放置的地方
* script：程式邏輯放置的地方
* style：相關 css 標籤語法放置的地方
    
所以這邊就可以很清楚了解，在 Vue3 的設計上，每一個網頁可以當作一個 .vue 檔案，而這一個 .vue 檔案要顯示的頁面內容，會放在 <template></template> 裡面，相關的程式邏輯語法會放在 <script></script> 裡面，最後如果有相關的 css 樣式，則放在 <style></style>。

**Vue3 - 從零開始學 - Day2 [完]**