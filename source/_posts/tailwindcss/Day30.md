---
title: tailwindcss 從零開始學¹ - Day30 - Daisyui
date: 2023-10-07 09:05:03
tags:
---
其實 tailwindcss 寫久了，就會發現原始碼會充滿著 css 的樣式屬性，在維護上不是那樣方便。但現在也有非常多基於 tailwindcss 的框架，這個單元要來介紹 Daisyui 就是這樣的一個框架。

它可以把一個複雜的元件：

```html
<button class="bg-indigo-600 px-4 py-3 text-center text-sm font-semibold inline-block text-white cursor-pointer uppercase transition duration-200 ease-in-out rounded-md hover:bg-indigo-700 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-indigo-600 focus-visible:ring-offset-2 active:scale-95">
  Tailwind Button
</button>
```

省略變成：

```html
<button class="btn btn-primary">
  daisyUI Button
</button>
```

但這樣又會變成跟 Bootstrap 不是一樣嗎？直接使用 Bootstrap 就好了啊？

但因為 Daisyui 是以插件的形式存在於 tailwindcss，所以變成是兩個框架可以共同使用，例如：

```html
<button class="btn btn-primary w-64">
  daisyUI Button
</button>
```

可以同時使用 Daisyui 與 tailwindcss ，其威力更加強大，也幫助省了非常多的時間。

Daisyui 的安裝方式，一樣在專案目錄下執行命令：

```bash
npm i -D daisyui@latest
```

修改 tailwind.config.js：

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}", "./dist/**/*.html"],
  theme: {

  },
  plugins: [require("daisyui")],
}
```

那這個單元簡單介紹一個側邊欄位跟 header 欄位的排版方式：

```html
<div class="drawer lg:drawer-open">
  <input id="my-drawer-3" type="checkbox" class="drawer-toggle" />
  <div class="drawer-content flex flex-col">
    <!-- Navbar -->
    <div class="navbar bg-base-300 w-full">
      <div class="flex-none lg:hidden">
        <label for="my-drawer-3" aria-label="open sidebar" class="btn btn-square btn-ghost">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block h-6 w-6 stroke-current"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
        </label>
      </div>
      <div class="mx-2 flex-1 px-2">Navbar Title</div>
      <div class="hidden flex-none lg:block">
        <ul class="menu menu-horizontal">
          <!-- Navbar menu content here -->
          <li><a>Navbar Item 1</a></li>
          <li><a>Navbar Item 2</a></li>
        </ul>
      </div>
    </div>
    <!-- Page content here -->
    Content
  </div>
  <div class="drawer-side">
    <label for="my-drawer-3" aria-label="close sidebar" class="drawer-overlay"></label>
    <ul class="menu bg-base-200 min-h-full w-80 p-4">
      <!-- Sidebar content here -->
      <li><a>Sidebar Item 1</a></li>
      <li><a>Sidebar Item 2</a></li>
    </ul>
  </div>
</div>
```

呈現效果：

![https://ithelp.ithome.com.tw/upload/images/20231007/20162607d3PTf8jEo7.png](https://ithelp.ithome.com.tw/upload/images/20231007/20162607d3PTf8jEo7.png)

-----

至此

tailwindcss - 從零開始學 30 天之旅結束拉！

首先先回顧一下這 30 天的內容：

專案建立：

[tailwindcss - 從零開始學 - Day1 - 為何而戰](https://ithelp.ithome.com.tw/articles/10315916)
[tailwindcss - 從零開始學 - Day2 - 設定環境](https://ithelp.ithome.com.tw/articles/10316208)

基本用法：

[tailwindcss - 從零開始學 - Day3 - 文字](https://ithelp.ithome.com.tw/articles/10316491)

基本元件：

[tailwindcss - 從零開始學 - Day4 - 一個簡單的按鈕](https://ithelp.ithome.com.tw/articles/10316799)
[tailwindcss - 從零開始學 - Day5 - header](https://ithelp.ithome.com.tw/articles/10317334)
[tailwindcss - 從零開始學 - Day6 - header RWD](https://ithelp.ithome.com.tw/articles/10317687)
[tailwindcss - 從零開始學 - Day7 - 橫幅排版](https://ithelp.ithome.com.tw/articles/10318159)
[tailwindcss - 從零開始學 - Day8 - 卡片排版](https://ithelp.ithome.com.tw/articles/10318164)
[tailwindcss - 從零開始學 - Day9 - 卡片排版組合](https://ithelp.ithome.com.tw/articles/10318166)
[tailwindcss - 從零開始學 - Day10 - 卡片排版](https://ithelp.ithome.com.tw/articles/10318167)
[tailwindcss - 從零開始學 - Day11 - 卡片排版](https://ithelp.ithome.com.tw/articles/10318168)
[tailwindcss - 從零開始學 - Day12 - 卡片排版](https://ithelp.ithome.com.tw/articles/10319476)

版面排版：

[tailwindcss - 從零開始學 - Day13 - Dashboard 排版](https://ithelp.ithome.com.tw/articles/10319494)
[tailwindcss - 從零開始學 - Day14 - Dashboard 排版](https://ithelp.ithome.com.tw/articles/10320778)
[tailwindcss - 從零開始學 - Day15 - 三列式排版](https://ithelp.ithome.com.tw/articles/10324850)
[tailwindcss - 從零開始學 - Day22 - 登入畫面](https://ithelp.ithome.com.tw/articles/10330592)

表單元件：

[tailwindcss - 從零開始學 - Day16 - 表單輸入](https://ithelp.ithome.com.tw/articles/10325577)
[tailwindcss - 從零開始學 - Day17 - 表單 icon](https://ithelp.ithome.com.tw/articles/10326481)
[tailwindcss - 從零開始學 - Day18 - 表單 checkbox](https://ithelp.ithome.com.tw/articles/10327167)
[tailwindcss - 從零開始學 - Day19 - 表單全](https://ithelp.ithome.com.tw/articles/10328524)
[tailwindcss - 從零開始學 - Day24 - 表單 input 進階](https://ithelp.ithome.com.tw/articles/10332109)

表格元件：

[tailwindcss - 從零開始學 - Day20 - Table](https://ithelp.ithome.com.tw/articles/10328632)
[tailwindcss - 從零開始學 - Day21 - table 行列固定](https://ithelp.ithome.com.tw/articles/10329390)

滑鼠事件：

[tailwindcss - 從零開始學 - Day23 - Hover Group](https://ithelp.ithome.com.tw/articles/10331335)

[tailwindcss - 從零開始學 - Day25 - peer](https://ithelp.ithome.com.tw/articles/10332667)

設定檔案：

[tailwindcss - 從零開始學 - Day26 - 簡化標籤](https://ithelp.ithome.com.tw/articles/10333405)
[tailwindcss - 從零開始學 - Day27 - 設定檔](https://ithelp.ithome.com.tw/articles/10334039)

安裝插件：

[tailwindcss - 從零開始學 - Day28 - 使用插件](https://ithelp.ithome.com.tw/articles/10334640)
[tailwindcss - 從零開始學 - Day29 - 下拉式選單插件](https://ithelp.ithome.com.tw/articles/10334647)
[tailwindcss - 從零開始學 - Day30 - Daisyui](https://ithelp.ithome.com.tw/articles/10335806)

雖然稱不上什麼大作的文章，但也算是屬於自己的學習筆記，這真的是一種很棒的學習方式，邊學邊寫，然後分享。

那麼 tailwindcss - 從零開始學 結束了嗎？

這邊只是學習如何製作網頁版型與元件，接下來還必須要跟前端程式語言框架整合，例如 Vue3。才算是一個完整的前端開發的學習之路。

希望未來還有機會用這樣的方式跟大家見面。

恭喜自己完賽～！！

**tailwindcss 從零開始學¹ - 本季[終]**