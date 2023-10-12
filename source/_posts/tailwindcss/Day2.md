---
title: tailwindcss 從零開始學¹ - Day2 - 設定環境
date: 2023-09-09 09:22:27
tags:
---
上一個單元了解了為何要使用 tailwindcss 與其好處，接下來第一件事情一定是建立專案，要使用 tailwindcss 的方式有很多種，最快的方式就是直接使用 CDN，將 CSS 檔案直接引入，如：

```html
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
  <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
</body>
</html>
```

直接在原始的 html 檔案引用：

```html
<script src="https://cdn.tailwindcss.com"></script>
```

然後就可以直接使用其 class name：

```html
<h1 class="text-3xl font-bold underline">
    Hello world!
</h1>
```

這樣雖然可以直接快速的使用，但缺點就是引入的檔案會非常大，等於是引入了所有 tailwindcss 的 class，在網頁的讀取的效率會很差。

所以這邊要介紹最常使用的方式，就是使用編譯的方式，也就是用到哪些 class name ，輸出成一個單一的 css 檔案，這樣做的好處是會大幅減少這個 css 檔案的大小。不在需要引用一整包大包的 css 檔案，但這個方式會需要一些步驟來安裝。

### 安裝

安裝的所有步驟都會使用終端機來執行命令，開啟終端機之後就可以開始以下的步驟。

新建一個資料夾：

```shell
$ mkdir tailwindcss-demo
```

專案初始化：

```shell
$ npm init -y
```

這邊使用 npm 來安裝， -y 表示跳過所有提示步驟，如果不輸入 -y 則會需要一個一個的問題確認，這些問題是關於這個專案的一些資訊，通常都會直接略過而使用初始化的內容。

安裝套件：

```shell
$ npm i -D tailwindcss postcss autoprefixer
```

這邊安裝 tailwindcss 的版本會是 v3.1.8，而 postcss 與 autoprefixer 則是 tailwindcss 編譯時會使用到的兩個產生 css 的工具，這邊就不多做介紹。

產生配置檔案：

```shell
$ npx tailwindcss init -p
```

輸入完之後會產生兩個檔案：tailwind.config.js 與 postcss.config.js。

* tailwind.config.js：會放相關的 html 檔案與 js 檔案路徑，或者一些客製化的設定。
    
* postcss.config.js：會放 postcss 插件的設定。

接下來稍微整理一下檔案，先新增一個資料夾 src，然後新增一個 tailwind.css 檔案，把 tailwind.css 放在資料夾 src 底下，並且輸入：

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

編譯 tailwindcss 時，會參考這個檔案的編譯來源，來產生對應的 css 功能。

接下來新增一個資料夾 dist，然後新增一個 index.html 然後把 這個檔案放在資料夾 dist 底下，並且輸入：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link href="style.css" rel="stylesheet">
</head>

<body>
    <h1 class="text-3xl font-bold underline">
        Hello world!
    </h1>
</body>

</html>
```

所以剛剛的動作，用 Visual Studio Code 開啟之後，整個專案結構會變成：

![https://ithelp.ithome.com.tw/upload/images/20230909/201626073kLqMl7yyQ.png](https://ithelp.ithome.com.tw/upload/images/20230909/201626073kLqMl7yyQ.png)

這邊會發現還沒有產生 style.css，所以開啟這個 index.html 檔案是沒有任何效果的。而在這個時候 tailwind.config.js 就會發揮功能，tailwind v3 會檢查 tailwind.config.js 內的 html 與 js 相關檔案的路徑，而去檢查這些檔案內所引用到的 tailwindcss 的功能，經由編譯之後統一放到所輸出的 css 檔案內。簡單講就是有用到的 class 功能，才會產生對應的 class。

修改 tailwind.config.js：

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}", "./dist/**/*.html"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

這邊的 content 就是設定要編譯的檔案範圍，./src/\*\*/\*.{html,js} 就表示會讀取在 src 資料夾底下的所有 html 與 js 檔案。所以 src 資料夾內可以放入其它的 js 檔案，但在這邊先不放入任何 js 檔案。

因為我將 index.html 放在 dist 這個資料夾內，所以會寫成 ./dist/\*\*/\*.html 就表示會讀取在 dist 資料夾底下的所有 html 檔案。

進行編譯：

```shell
$ npx tailwindcss -i ./src/tailwind.css -o ./dist/style.css
```

編譯成功後會在 dist 資料夾底下產生 style.css ，直接用瀏覽器打開 index.html 就可以看到結果。

為了編譯方便，不用一直重複輸入上述指令，可以將編譯指令放入到 package.json：

```json
"scripts": {
    "build": "tailwindcss -i ./src/tailwind.css -o ./dist/style.css"
},
```

然後執行以下指令可以重新編譯

```shell
$ npm run build
```

上面編譯的方式，是每次修改 html 時，都要重新執行編譯指令，其實相當不方便。如果希望修改 html 檔案，存擋之後可以自動編譯，可以新增以下指令到 package.json：

```json
"scripts": {
    "watch": "tailwindcss -i ./src/tailwind.css -o ./dist/style.css --watch"
},
```

然後執行：

```shell
$ npm run watch
```

如此一來，當 html 檔案經過修改後，且進行儲存，就會自動重新編譯，不需要再重新輸入編譯的指令，只要去瀏覽器重新整理就可以看到修改後的結果。

**tailwindcss 從零開始學¹ - Day2 [完]**