---
title: tailwindcss 從零開始學¹ - Day27 - 設定檔
date: 2023-10-04 12:55:58
tags:
---
這個單元要來介紹 tailwindcss 的設定檔案。

在專案結構中有一個檔案為 tailwind.config.js：

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}", "./dist/**/*.html"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

在這份檔案之中，目前只有設定 content 的位置，這個設定主要是建立 tailwindcss 要編譯的來源檔案，可以回頭去參考 [tailwindcss - 從零開始學 - Day2 - 設定環境](https://ithelp.ithome.com.tw/articles/10316208)。

在這個設定檔案，可以去定義自己想要的顏色：

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}", "./dist/**/*.html"],
  theme: {
    colors: {
      'blue': '#1fb6ff',
    },
    extend: {},
  },
  plugins: [],
}
```

在這裡定義了 `color` 內有一個顏色 `'blue': '#1fb6ff'`，然後就可以使用 `bg-blue` 或者 `text-blue` 使用這個顏色：

```html
<h1 class="bg-blue">Hello World</h1>
```

但這個時候會發現 tailwindcss 原本提供的顏色就無法使用了，如：

```html
<a href="/#" class="px-12 py-3 text-lg bg-blue text-white border border-black rounded hover:bg-transparent hover:text-indigo-600">新增</a>
```

這個範例的 `bg-blue` 起了做用，但是 `hover:bg-transparent` 與 `hover:text-indigo-600` 卻無法使用了。

要解決這個問題，可以另外新增：

```js
/** @type {import('tailwindcss').Config} */
const colors = require('tailwindcss/colors');

module.exports = {
  content: ["./src/**/*.{html,js}", "./dist/**/*.html"],
  theme: {
    colors: {
      transparent: 'transparent',
      indigo: colors.indigo,
      'blue': '#1fb6ff',
    },
    extend: {},
  },
  plugins: [],
}
```

這裡使用 `require('tailwindcss/colors');` 將系統顏色引用近來，並且定義了 `transparent: 'transparent'` 與 `indigo: colors.indigo` 兩個顏色，這樣就可以使用 `hover:bg-transparent` 與 `hover:text-indigo-600` 這兩種顏色了。

但如果要想要保留系統所有顏色，並且新增一些自定義的顏色，這樣就必須要一個一個引用也是非常麻煩，可以直接在 `extend` 定義自己想要的顏色即可：

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}", "./dist/**/*.html"],
  theme: {
    extend: {
      colors: {
        'blue': '#1fb6ff',
      },
    },
  },
  plugins: [],
}
```

如此一來保有了所有系統顏色，並且新增一組顏色 `'blue': '#1fb6ff'`。

而在顏色的定義之中，也可以模仿系統的顏色設定一樣，有 100 ~ 900 這樣的命名空間，如：

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}", "./dist/**/*.html"],
  theme: {
    extend: {
      colors: {
        'blue': '#1fb6ff',
        'tahiti': {
          100: '#cffafe',
          200: '#a5f3fc',
          300: '#67e8f9',
          400: '#22d3ee',
          500: '#06b6d4',
          600: '#0891b2',
          700: '#0e7490',
          800: '#155e75',
          900: '#164e63',
        },
      },
    },
  },
  plugins: [],
}
```

這樣就可以直接使用這個自訂的顏色 tahiti 空間範圍從 100 ~ 900：

```html
<h1 class="bg-tahiti-400">Hello World</h1>
```

[今日完整範例](https://play.tailwindcss.com/7iTnALBjea?layout=horizontal)

**tailwindcss 從零開始學¹ - Day27 [完]**