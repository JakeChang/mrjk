---
title: tailwindcss 從零開始學¹ - Day4 - 一個簡單的按鈕
date: 2023-09-11 09:35:29
tags:
---
在真正進入到網頁排版之前，還必須弄清楚一些事情，這個單元先從一個簡單的按鈕開始，透過製作一個按鈕，進而推展到製作各種組件，最後才是排版。

首先一開始，先寫一個按鈕的基本雛型：

```html
<div>
  <a class="" href="/">Button</a>
</div>
```

不管是元件的製作或者是排版，一開始最重要的是設定邊界，稱為 padding，稱為內部邊界，官方文件在這：[https://tailwindcss.com/docs/padding](https://tailwindcss.com/docs/padding)。

使用關鍵字 p 開頭，例如 p-4，就表示元件與上下左右距離 4，p-4 在 CSS 定義上表示：

```css
padding: 1rem; /* 16px */
```

另外也可以針對某一個方位來 padding，例如針對上方 padding，可以用 pt-。

以下是幾的簡單的範例：

* pt-6：針對上方 padding 6
* pr-4：針對右邊 padding 4
* pb-8：針對下方 padding 8
* pl-2：針對左邊 padding 2
    
當然，後面的數字越大表示 padding 越大，範例：

```html
<div class="pt-6 ...">pt-6</div>
<div class="pr-4 ...">pr-4</div>
<div class="pb-8 ...">pb-8</div>
<div class="pl-2 ...">pl-2</div>
```

如果同時有針對某兩個方位 padding，如右邊與左邊，可以精簡成 px-。

* px-12：針對 x 軸 padding 12
* py-3：針對 y 軸 padding 3
    
將 padding 套用到一開始的按鈕的範例，並且新增上一個單元介紹的文字大小：

```html
<div>
  <a class="px-12 py-3 text-lg" href="/">Button</a>
</div>
```

接下來增加按鈕的背景顏色與文字顏色，官方文件：

* 背景顏色：[https://tailwindcss.com/docs/background-color](https://tailwindcss.com/docs/background-color)
* 文字顏色：[https://tailwindcss.com/docs/text-color](https://tailwindcss.com/docs/text-color)
    
這邊我挑了 `bg-blue-500` 這個藍色的背景顏色與 `text-white` 白色文字，所以按鈕的樣式會修改成：

```html
<div>
  <a class="px-12 py-3 text-lg bg-blue-500 text-white" href="/">Button</a>
</div>
```

接下來新增邊框的大小與顏色：

* 邊框大小：[https://tailwindcss.com/docs/border-width](https://tailwindcss.com/docs/border-width)
* 邊框顏色：[https://tailwindcss.com/docs/border-color](https://tailwindcss.com/docs/border-color)

這邊我挑了 `border` 這個邊框大小，它會設定邊框為 1px。邊框顏色為 `border-black` 黑色，所以按鈕的樣式會修改成：

```html
<div>
  <a class="px-12 py-3 text-lg bg-blue-500 text-white border border-black" href="/">Button</a>
</div>
```

接下來，增加按鈕的圓角弧度：

* 圓角：[https://tailwindcss.com/docs/border-radius](https://tailwindcss.com/docs/border-radius)

這邊我挑了 `rounded` 這個圓角，是一個最基本的圓角。所以按鈕的樣式會修改成：

```html
<div>
  <a class="px-12 py-3 text-lg bg-blue-500 text-white border border-black rounded" href="/">Button</a>
</div>
```

接下來增加一個滑鼠移動到按鈕上方，會自動變色的效果，只要使用 `hover:` 這個關鍵名稱，冒號後面帶入任何顏色即可，例如 `hover:bg-transparent` 當滑鼠移動到上方，會把背景變成透明，`hover:text-indigo-600` 當滑鼠移動到上方，會把文字變成紫色。所以按鈕的樣式會修改成：

```html
<div>
  <a class="px-12 py-3 text-lg bg-blue-500 text-white border border-black rounded hover:bg-transparent hover:text-indigo-600" href="/">Button</a>
</div>
```

這邊關於 hover 的文件可以到這裡參考：[https://tailwindcss.com/docs/hover-focus-and-other-states](https://tailwindcss.com/docs/hover-focus-and-other-states)。

最後，這個按鈕只會顯示在左上角，我想要讓這個按鈕放在螢幕的正中央，必須要在外圍的 div 加入以下 class：

```html
<div class="flex h-screen items-center justify-center">
  <a class="px-12 py-3 text-lg bg-blue-500 text-white border border-black rounded hover:bg-transparent hover:text-indigo-600" href="/">Button</a>
</div>
```

* h-screen：將整體的高度設定為螢幕的高度，也就是說螢幕多高，div 就有多高。
* items-center：垂直置中。
* justify-center：水平置中。
* flex：要讓置中產生效果，必須要加入 flex，就是可以橫向排版，關於 flex 在後續的單元會繼續討論。

這樣一個基本的按鈕就完成了。

[今日完整範例](https://play.tailwindcss.com/fze8G2JJ1z)

**tailwindcss 從零開始學¹ - Day4 [完]**