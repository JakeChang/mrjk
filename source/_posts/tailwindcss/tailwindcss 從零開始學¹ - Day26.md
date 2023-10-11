---
title: tailwindcss 從零開始學¹ - Day26 - 簡化標籤
date: 2023-10-03 12:29:36
tags:
---
如果真的有一步一步看過這個系列的教學文章，可以發現在 tailwindcss 的世界中，雖然可以很清楚的了解每一個元件的命名以及異議，例如：`w-32` 就表示寬度、`bg-blue-500` 就表示背景顏色。我們可以很容易地寫出 UI 元件，例如以下是一個按鈕元件：

```html
<div class="flex min-h-screen w-screen flex-row items-center justify-center gap-4">
  <a href="/#" class="flex w-32 items-center justify-center rounded-lg bg-blue-500 px-4 py-2 text-sm font-medium text-white hover:bg-blue-700">新增</a>
</div>
```

這個按鈕會呈現這個樣子，而且滑鼠移動過去也會產生變色效果：

![https://ithelp.ithome.com.tw/upload/images/20231003/20162607Z0BYSU7JQL.png](https://ithelp.ithome.com.tw/upload/images/20231003/20162607Z0BYSU7JQL.png)

但隨著專案越長越大，會發現整個 html 都會呈現滿滿的 tailwindcss 的標籤語法，看起來會非常複雜與髒亂感。

tailwindcss 在發明的時候就已經發現這個問題了，所以這裡可以直接使用 `@apply` 來解決這個問題。

回到 [tailwindcss - 從零開始學 - Day2 - 設定環境](https://ithelp.ithome.com.tw/articles/10316208)，在這個單元介紹了如何設定一個新的 tailwindcss 的專案，而在過程之中會新增一個 tailwind.css 的檔案：

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

可以將上述的按鈕元件的標籤在這裡用一個名稱來包裝起來，這裡要使用的就是 `@apply`：

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

.btn {
    @apply flex w-32 items-center justify-center rounded-lg bg-blue-500 px-4 py-2 text-sm font-medium text-white hover:bg-blue-700
}
```

在這裡直接命名一個 .btn，並且使用 `@apply` 關鍵字，將所有按鈕用到的樣式放在後面。

然後回到按鈕直接修改成：

```html
<a href="/#" class="btn">新增</a>
```

這樣不僅可以美化整體的 html 檔案，更加清楚與乾淨，而在專案的開發上確實也會這樣實作，設計師會定義好每個元件的樣式，而我們就將這些定義好的樣式宣告在 tailwind.css 裡頭，在外部的 html 檔案就可以直接呼叫使用了。

[今日完整範例](https://play.tailwindcss.com/Y8OdZAU5xE?layout=horizontal)

**tailwindcss 從零開始學¹ - Day26 [完]**