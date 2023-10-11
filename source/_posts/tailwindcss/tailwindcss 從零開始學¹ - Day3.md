---
title: tailwindcss 從零開始學¹ - Day3 - 文字
date: 2023-09-10 12:56:07
tags:
---
上一個單元已經學會了如何安裝與設定一個新的專案，在進入真正的 UI 開發之前，如果只是想要單純測試某些 UI 樣板，而又不想使用上一個單元的方式建立專案，則可以到 [https://play.tailwindcss.com/](https://play.tailwindcss.com/) 來測試任何關於 tailwindcss 的樣板。

進入這個網址之後，可以先把左邊所有的 html 標籤刪除掉，然後放上：

```html
<h1 class="text-3xl font-bold underline">Hello world!</h1>
```

而在右側欄位就可以即是顯示這個標籤在網頁上的呈現效果，是不是非常方便呢？

### 文字

首先，第一步就先從文字開始吧。

文字顯示的用法，在官方文件其實寫得非常清楚，包含所有的文字屬性與範例用法，進入 [https://tailwindcss.com/docs/](https://tailwindcss.com/docs/) 在左側的分類可以找到 Typography，有非常多關於文字的用法，先來看看如何調整文字。

文字大小：

```html
<p class="text-basic">Hello World</p>
```

tailwindcss 的使用方式非常簡單，直接指定 class name 即可，這邊指定 text-base 這個名稱，在官網的文件上都會寫出在 CSS 的原始定義，所以 text-basic 就表示：

```css
font-size: 1rem; /* 16px */
line-height: 1.5rem; /* 24px */
```

詳細可以參考官方文件：[https://tailwindcss.com/docs/font-size](https://tailwindcss.com/docs/font-size)。在文件上還可以找到更多關於文字大小的 class name，總共有下面這些調整字型大小的標籤可以使用：

* text-xs
* text-sm
* text-base
* text-lg
* text-xl
* text-2xl
* text-3xl
* text-4xl
* text-5xl
* text-6xl
* text-7xl
* text-8xl
* text-9xl

文字粗細：

```html
<p class="font-medium">Hello World</p>
```

一樣可以到官方文件參考：[https://tailwindcss.com/docs/font-weight](https://tailwindcss.com/docs/font-weight)。

總共有下面這些調整字型粗細的標籤可以使用：

* font-thin
* font-extralight
* font-light
* font-normal
* font-medium
* font-semibold
* font-bold
* font-extrabold
* font-black

這邊就不一個一個展示其效果如何，大家可以自己去 [https://play.tailwindcss.com/](https://play.tailwindcss.com/) 試試看這些文字的效果如何。

最後列出三個常用的關於文字的標籤，文字對齊、文字顏色與文字裝飾。

文字對齊：

```html
<p class="text-right">Hello World</p>
```

* 官方文件：[https://tailwindcss.com/docs/text-align](https://tailwindcss.com/docs/text-align)
    
文字顏色：

```html
<p class="text-blue-600">Hello World</p>
```

* 官方文件：[https://tailwindcss.com/docs/text-color](https://tailwindcss.com/docs/text-color)
    
文字裝飾：

```html
<p class="underline">Hello World</p>
```

* 官方文件：[https://tailwindcss.com/docs/text-decoration](https://tailwindcss.com/docs/text-decoration)
    
這個單元介紹了 tailwindcss 的一些文字的基本用法，關於一些對齊的方式，後面的單元介紹真正的排版例子時，再來討論會比較清楚這些用法。

**tailwindcss 從零開始學¹ - Day3 [完]**