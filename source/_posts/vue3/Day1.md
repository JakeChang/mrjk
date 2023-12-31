---
title: Vue3 從零開始學¹ - Day1 - 建立專案
date: 2023-09-01 12:51:50
tags: vue3
---

### 關於鐵人賽

進入業界已經第 16 年，回想剛接觸電腦的那一年，在電腦螢幕面前編輯 HTML 的那種成就感，一直到現在依舊在工程師的崗位奮戰中。而如今在 Web 開發上已經大不同，從最早期的 ASP 時代到 ASP.NET 再到 JSP，歷經這些開發工具的推陳出新，也就代表著開發時代已經進入全新領域。

大叔開發經驗十幾年，只要學習到一個全新的領域或工具，都會撰寫給自己看的文件，因為腦容量真的有限，記不了太多東西了，所以希望藉由這個比賽，把過去的筆記整理出來，除了給未來的自己看之外，也讓想要學習的朋友有個參考。

所以參加鐵人賽，就是再次把自己的筆記再度重新回歸腦內咀嚼，然後產出、分享。

### 前言

這個「Vue3-從零開始學」的系列，是一個關於 Vue3 的學習入門，我將會分享關於學習 Vue3 的一切基礎，所以非常適合從零開始想要接觸前端開發的朋友。

所以 Vue3 是一個前端的開發框架，有了這個框架，開發人員更可以專心在網頁的開發，而不用分心處理跟資料庫的資料溝通，畢竟那是後端工程師或者資料庫工程師的範疇，~~推卸責任~~。

關於前後端分離這件事情，之後的單元再來慢慢分享我的觀點。

那麼學習 Vue3 需要會什麼樣的技術背景？

一點點的 HTML、一點點的 CSS 跟一點點的 JavaScript，就算完全沒有接觸過網頁開發，我也會希望可以藉由這個系列幫助到大家真的可以完全從不會到會。

Vue3 是一個前端開發者可以學習的框架，在前端框架數量爆炸的現今，除了 Vue3 之外，還有 React、Next.js 等框架可以來使用。至於為何我選擇 Vue3 來學習，不外乎業界也在用、容易學習、屬於 JS 語法等各種理由，最重要的一個理由就是搭建快速，只要一點點的程式語法，就可以讓網頁動了起來，對於完全不會的人，只要做一點點事情就可以充滿成就感，這個真的是很重要的一件事情。

最後，因為我是使用 MacBook 的一個開發者，所以操作介面都是以 Mac 為主要的操作介面，這點還請各位讀者見諒。

所以不囉唆，首先，第一個單元就是建立專案。

### 建立專案

任何程式語言的開發第一步，都是建立一個新的專案，在 Vue3 的世界可以使用一個標準工具來建立專案，就是 Vue CLI 工具，這裡是它的官網：[https://cli.vuejs.org](https://cli.vuejs.org/#getting-started)，讀者可以自行參考。

接下來的步驟，必須使用指令來執行所有命令，所以直接開啟終端機，安裝 Vue CLI：

```bash
sudo npm install -g @vue/cli
```

安裝完成後，確認版本：

```bash
vue -V
```

會出現這一行，說明目前所安裝的版本：

```bash
@vue/cli 5.0.8
```

就表示安裝完成了。

### 新增專案

接下來就可以使用 vue 命令來新增專案，可以先到你要的目錄下，在這裡我是到桌面上來新增：

```bash
cd ~/Desktop
```

然後直接輸入：

```bash
vue create vue-demo
```

vue create 就表示要新增一個新的專案，然後接上專案的名稱，這邊名稱可以自由命名，我在此命名為 vue-demo。

在新增專案的過程之中，選擇 Vue3 即可：

```bash
Vue CLI v5.0.8
? Please pick a preset:
❯ Default ([Vue 3] babel, eslint)
  Default ([Vue 2] babel, eslint)
  Manually select features
```

接下來畫面會開始執行安裝的過程，如果安裝成功，可以看到這些內容：

```bash
...前略...

📄  Generating README.md...

🎉  Successfully created project vue-demo.
👉  Get started with the following commands:

 $ cd vue-demo
 $ npm run serve
```

恭喜你，專案成功建立。

接下來，要開始執行這個新的專案，直接進入該目錄底下：

```bash
cd vue-demo/
npm run serve
```

就會開始啟動專案，啟動完成會看到以下內容：

```bash
App running at:
  - Local:   http://localhost:8081/
  - Network: http://192.168.0.211:8081/

  Note that the development build is not optimized.
  To create a production build, run npm run build.
```

這個時候直接開啟瀏覽器，在網址輸入：[http://localhost:8080/](http://localhost:8080/) 即可以看到 Vue3 專案內容，也就是這個畫面：

![https://ithelp.ithome.com.tw/upload/images/20230901/20162607ngBDs4pCrp.png](https://ithelp.ithome.com.tw/upload/images/20230901/20162607ngBDs4pCrp.png)

在瀏覽器看到這畫面，就代表專案成功執行，大功告成。

接下來 Day2 會探討這個 Vue3 的專案結構。

**Vue3 從零開始學¹ - Day1 [完]**