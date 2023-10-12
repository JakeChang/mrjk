---
title: tailwindcss 從零開始學¹ - Day23 - Hover Group
date: 2023-09-30 10:51:07
tags:
---
這個單元來討論 hover 的進階用法，在之前的 [Day4 - 一個簡單的按鈕](https://ithelp.ithome.com.tw/articles/10316799) 已經了解到當滑鼠移動到會產生事件行為需要使用 `hover:`，後面可以接上任何的屬性樣式，例如：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <button class="rounded-lg bg-sky-500 p-2 text-white hover:bg-sky-700">Button</button>
</div>
```

在這個例子之中，原本的按鈕背景顏色為 `bg-sky-500`，加上 `hover:bg-sky-700` ，表示滑鼠移動到上方按鈕背景顏色會變成 `bg-sky-700`，這個 `hover:` 的用法已經非常了解了。

但有時候會有一個非常複雜的按鈕 div 標籤，例如：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <a href="#" class="max-w-xs space-y-3 rounded-lg bg-white p-6 shadow-lg ring-1 ring-slate-900/5">
    <div class="flex items-center space-x-3">
      <h3 class="text-sm font-semibold text-slate-900">Title</h3>
    </div>
    <p class="text-sm text-slate-500">Sub Title 1234567890</p>
  </a>
</div>
```

目前會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20230930/20162607XEkXwXqlgA.png](https://ithelp.ithome.com.tw/upload/images/20230930/20162607XEkXwXqlgA.png)

在這個例子之中，會希望當滑鼠移動到上方時，會希望整個卡片背景顏色會有變化，文字也想要變成白色，所以按照學習到 `hover:` 的用法，可能會這樣寫：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <a href="#" class="max-w-xs space-y-3 rounded-lg bg-white p-6 shadow-lg ring-1 ring-slate-900/5 hover:bg-sky-500 hover:ring-sky-500 hover:text-white">
    <div class="flex items-center space-x-3">
      <h3 class="text-sm font-semibold text-slate-900">Title</h3>
    </div>
    <p class="text-sm text-slate-500">Sub Title 1234567890</p>
  </a>
</div>
```

加入了三個 `hover:` 樣式，`hover:bg-sky-500`、`hover:ring-sky-500`、`hover:text-white`，但是當滑鼠移動到上方時，背景顏色改變了，但文字卻沒有變化。

寫法不對嗎？換個方式改：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <a href="#" class="max-w-xs space-y-3 rounded-lg bg-white p-6 shadow-lg ring-1 ring-slate-900/5 hover:bg-sky-500 hover:ring-sky-500">
    <div class="flex items-center space-x-3">
      <h3 class="text-sm font-semibold text-slate-900 hover:text-white">Title</h3>
    </div>
    <p class="text-sm text-slate-500 hover:text-white">Sub Title 1234567890</p>
  </a>
</div>
```

分別在文字加入 `hover:text-white`，但結果卻造成滑鼠一定要移動到文字上方，其顏色才會變成白色：

![https://ithelp.ithome.com.tw/upload/images/20230930/20162607uaN1JW8yN6.png](https://ithelp.ithome.com.tw/upload/images/20230930/20162607uaN1JW8yN6.png)

這樣的效果也不是我們想要的。

好在，tailwindcss 提供了 `group` 來解決這個問題，所以必須要在最外層加入 `group`，並且在內部的子層結構加入 `group-hover:` 表示會隨著外層定義的 `group` 一起被宣告成 `:hover` 而產生變化。

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <a href="#" class="max-w-xs space-y-3 rounded-lg bg-white p-6 shadow-lg ring-1 ring-slate-900/5 hover:bg-sky-500 hover:ring-sky-500 group">
    <div class="flex items-center space-x-3">
      <h3 class="text-sm font-semibold text-slate-900 group-hover:text-white">Title</h3>
    </div>
    <p class="text-sm text-slate-500 group-hover:text-white">Sub Title 1234567890</p>
  </a>
</div>
```

在 a 標籤內宣告 `group`，然後在文字內宣告 `group-hover:text-white` ，就可以一同產生 `:hover` 變化。

最後的結果：

![https://ithelp.ithome.com.tw/upload/images/20230930/20162607fzXeMnIJ8O.png](https://ithelp.ithome.com.tw/upload/images/20230930/20162607fzXeMnIJ8O.png)

[今日完整範例](https://play.tailwindcss.com/T00TmpLJcc)

**tailwindcss 從零開始學¹ - Day23 [完]**