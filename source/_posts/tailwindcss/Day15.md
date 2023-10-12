---
title: tailwindcss 從零開始學¹ - Day15 - 三列式排版
date: 2023-09-22 12:40:16
tags:
---
上一個單元介紹了左右兩側的排版，這個單元要來介紹三列式的排版，並且三列都各自獨立有自己的滑動視窗，完成之後會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20230922/20162607l00ZDKm57l.png](https://ithelp.ithome.com.tw/upload/images/20230922/20162607l00ZDKm57l.png)

首先，老樣子，宣告 `div` 的架構：

```html
<div class="">
  <div class="">left</div>
  <div class="">medium</div>
  <div class="">right</div>
</div>
```

加入寬度高度屬性：

```html
<div class="h-screen w-full">
  <div class="">left</div>
  <div class="">medium</div>
  <div class="">right</div>
</div>
```

因為三列都呈現水平排版，所以使用 `flex` 與 `flex-row`：

```html
<div class="flex h-screen w-full flex-row">
  <div class="">left</div>
  <div class="">medium</div>
  <div class="">right</div>
</div>
```

加入三列的各自寬度，`w-??/12` 最大寬度可以設定到 12，所以這裡就平均分配為 `w-2/12` 與 `w-3/12` 與 `w-7/12`：

```html
<div class="flex h-screen w-full flex-row">
  <div class="w-2/12">left</div>
  <div class="w-3/12">medium</div>
  <div class="w-7/12">right</div>
</div>
```

目前會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20230922/20162607qn3dwFhQWS.png](https://ithelp.ithome.com.tw/upload/images/20230922/20162607qn3dwFhQWS.png)

為了讓三列可以區分的出來，這裡可以加入背景顏色，但我這裡使用另外一種分隔線，針對右邊顯示分隔線，`border-r-2`，並且設定分隔線的顏色為 `border-red-500`：

```html
<div class="flex h-screen w-full flex-row">
  <div class="w-2/12 border-r-2 border-red-500">left</div>
  <div class="w-3/12 border-r-2 border-red-500">medium</div>
  <div class="w-7/12">right</div>
</div>
```

加入 RWD 適應條件，最左邊的排版使用 `hidden`、`sm:flex`、`sm:w-2/12`，表示當寬度大於 sm ，會使用寬度 `flex`、`w-2/12`，小於 sm 會使用 `hidden`。

中間的排版使用 `hidden`、`sm:flex`，表示當寬度大於 sm ，會使用寬度 `flex`，小於 sm 會使用 `hidden`。

右邊的排版使用 `flex`、`w-full`、`sm:w-7/12`，表示當寬度大於 sm ，會使用寬度 `w-7/12`，小於 sm 會使用 `w-full`。

```html
<div class="flex h-screen w-full flex-row">
  <div class="border-r-2 border-red-500 hidden sm:flex sm:w-2/12">left</div>
  <div class="w-3/12 border-r-2 border-red-500 hidden sm:flex">medium</div>
  <div class="flex w-full sm:w-7/12">right</div>
</div>
```

最後一個條件是要讓三列都各自有自己的滑動視窗，使用 `overflow-y-scroll` 表示在 y 軸呈現可以滑動的狀態：

```html
<div class="flex h-screen w-full flex-row">
  <div class="border-r-2 border-red-500 hidden sm:flex sm:w-2/12 overflow-y-scroll">left</div>
  <div class="w-3/12 border-r-2 border-red-500 hidden sm:flex overflow-y-scroll">medium</div>
  <div class="flex w-full sm:w-7/12 overflow-y-scroll">right</div>
</div>
```

最後可以加入圖片來測試一下滑動狀態，另外為了讓圖片可以單獨呈現，所以加入了 `flex-col` 與 `gap-4`：

```html
<div class="flex h-screen w-full flex-row">
  <div class="hidden flex-col gap-4 overflow-y-scroll border-r-2 border-red-500 sm:flex sm:w-2/12">
    <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" />
    <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" />
    <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" />
    <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" />
    <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" />
    <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" />
  </div>
  <div class="w-3/12 border-r-2 border-red-500 hidden sm:flex overflow-y-scroll">medium</div>
  <div class="flex w-full sm:w-7/12 overflow-y-scroll">right</div>
</div>
```

[今日完整範例](https://play.tailwindcss.com/y7e5x1Rpri?layout=horizontal&size=1562x720)

**tailwindcss 從零開始學¹ - Day15 [完]**