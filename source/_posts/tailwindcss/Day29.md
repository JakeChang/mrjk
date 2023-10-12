---
title: tailwindcss 從零開始學¹ - Day29 - 下拉式選單插件
date: 2023-10-06 09:24:23
tags:
---
這個單元繼續來介紹其它好用的插件，下拉式選單插件。

首先一樣在專案目錄下安裝：

```bash
npm install tailwindcss-dropdown
```

然後在 tailwind.config.js 修改成：

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}", "./dist/**/*.html"],
  theme: {
  },
  variants: {
    display: ['responsive', 'dropdown']
  },
  plugins: [
    require('tailwindcss-dropdown'),
  ],
}
```

如果有使用多個插件，例如在 [tailwindcss - 從零開始學 - Day28 - 使用插件](https://ithelp.ithome.com.tw/articles/10334640) 介紹的文章閱讀版面插件，也是沒有問題的：

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}", "./dist/**/*.html"],
  theme: {

  },
  variants: {
    display: ['responsive', 'dropdown']
  },
  plugins: [
    require('@tailwindcss/typography'),
    require('tailwindcss-dropdown'),
  ],
}
```

接下來就可以來製作下拉式選單，一個最簡單的下拉式選單：

```html
<button class="relative dropdown:block">
  <a href=#>Sort</a>
  <ul class="hidden absolute left-0 w-auto">
    <li><a href=#>Ascending</a></li>
    <li><a href=#>Descending</a></li>
  </ul>
</button>
```

使用這個下拉式選單插件最主要的部分是加入樣式 `dropdown:block` 即可，所以在這裡按下 Sort 按鈕之後，在子層的兩個 `li` 就會被顯示出來。

但這樣的下拉式選單太過簡化，加入 tailwindcss 樣式來美化：

```html
<button class="dropdown:block text-medium relative rounded-lg border border-gray-300 bg-white px-3 py-2 text-gray-800 hover:border-gray-600" role="navigation" aria-haspopup="true">
  <div class="flex items-center">
    <span class="px-2 text-gray-700">Sort</span>
  </div>
  <ul class="absolute left-0 mt-3 hidden w-auto space-y-2 rounded-lg border border-gray-100 bg-white p-2 text-sm shadow-lg" aria-label="submenu">
    <a class="inline-block w-full rounded-md px-2 py-1 font-medium text-gray-600 hover:bg-gray-100 hover:text-gray-900" href="#"> Ascending </a>
    <a class="inline-block w-full rounded-md px-2 py-1 font-medium text-gray-600 hover:bg-gray-100 hover:text-gray-900" href="#"> Descending </a>
  </ul>
</button>
```

最後呈現的效果：

![https://ithelp.ithome.com.tw/upload/images/20231005/20162607HOq3vkNz1y.png](https://ithelp.ithome.com.tw/upload/images/20231005/20162607HOq3vkNz1y.png)

[今日完整範例](https://play.tailwindcss.com/JuWDn49RSY?layout=horizontal)

**tailwindcss 從零開始學¹ - Day29 [完]**