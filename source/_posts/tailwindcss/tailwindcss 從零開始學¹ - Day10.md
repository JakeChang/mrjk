---
title: tailwindcss 從零開始學¹ - Day10 - 卡片排版
date: 2023-09-17 20:25:38
tags:
---
這個單元繼續來介紹卡片排版的方式，前一個單元介紹了一種非常簡單的卡片排版，接下來要來介紹包含圖片的卡片排版方式。

一開始一樣宣告 div 標籤，與文字標籤：

```html
<div class="">
  <div class="">
    <p class="">title</p>
    <p class="">sub title</p>
  </div>
</div>
```

加入文字的樣式，與邊界 `p-4`：

```html
<div class="">
  <div class="p-4">
    <p class="text-4xl">title</p>
    <p class="mt-2 text-sm">sub title</p>
  </div>
</div>
```

接下來放上按鈕，這裡的按鈕樣式就不多做解說，跟之前的案例差不多：

```html
<div class="">
  <div class="p-4">
    <p class="text-4xl">title</p>
    <p class="mt-2 text-sm">sub title</p>
  </div>
  <div class="mt-4 flex justify-end p-4">
    <button type="button" class="rounded-lg bg-blue-700 px-4 py-2 text-white hover:bg-blue-200 hover:text-blue-700">下一頁</button>
  </div>
</div>
```

這個按鈕為了要讓它靠右，使用了 `flex` 與 `justify-end`。

接下來加入圖片：

```html
<div class="">
  <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" />
    
  <div class="p-4">
    <p class="text-4xl">title</p>
    <p class="mt-2 text-sm">sub title</p>
  </div>
  <div class="mt-4 flex justify-end p-4">
    <button type="button" class="rounded-lg bg-blue-700 px-4 py-2 text-white hover:bg-blue-200 hover:text-blue-700">下一頁</button>
  </div>
</div>
```

加入整個卡片的邊界 `m-4`，寬度 `w-1/5`，圓角 `rounded-lg` 與陰影 `shadow-lg`：

```html
<div class="m-4 w-1/5 rounded-lg shadow-lg">
  <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" />
    
  <div class="p-4">
    <p class="text-4xl">title</p>
    <p class="mt-2 text-sm">sub title</p>
  </div>
  <div class="mt-4 flex justify-end p-4">
    <button type="button" class="rounded-lg bg-blue-700 px-4 py-2 text-white hover:bg-blue-200 hover:text-blue-700">下一頁</button>
  </div>
</div>
```

但因為加入圖片的關係，上方的圓角會被圖片吃掉，所以圖片也要宣告上方為圓角，使用 `rounded-t-lg` 可以指定只有上方左右兩邊為圓角：

```html
<div class="m-4 w-1/5 rounded-lg shadow-lg">
  <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" class="rounded-t-lg" />

  <div class="p-4">
    <p class="text-4xl">title title title</p>
    <p class="mt-2 text-sm">sub titlesub titlesub titlesub titlesub titlesub titlesub titlesub titlesub titlesub titlesub titlesub titlesub title</p>
  </div>

  <div class="mt-4 flex justify-end p-4">
    <button type="button" class="rounded-lg bg-blue-700 px-4 py-2 text-white hover:bg-blue-200 hover:text-blue-700">下一頁</button>
  </div>
</div>
```

[今日完整範例](https://play.tailwindcss.com/m6J9TJQZmh?layout=horizontal&size=1000x720)

**tailwindcss 從零開始學¹ - Day10 [完]**