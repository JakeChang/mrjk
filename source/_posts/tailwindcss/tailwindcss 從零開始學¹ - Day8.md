---
title: tailwindcss 從零開始學¹ - Day8 - 卡片排版
date: 2023-09-15 15:03:00
tags:
---
接下來這個單元來製作一個簡單的卡片排版：

先宣告一些基本的排版：

```html
<a href="/">
    <div class="">
      <div>
        <p class="">My Title</p>
        <p class="">Description</p>
      </div>
    </div>
  </a>
```

會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20230914/20162607sCDHJVxPgQ.png](https://ithelp.ithome.com.tw/upload/images/20230914/20162607sCDHJVxPgQ.png)

然後加入跟文字屬性與留白屬性：

```html
 <a href="/">
    <div class="">
      <div>
        <p class="text-2xl font-bold">My Title</p>
        <p class="mt-4 text-lg font-medium">Description</p>
      </div>
    </div>
  </a>
```

會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20230914/20162607X0cCXlucAx.png](https://ithelp.ithome.com.tw/upload/images/20230914/20162607X0cCXlucAx.png)

加入外框屬性：

* rounded-3xl：圓角
* border-4：框線粗細
* border-black：框線顏色
    
```html
<a href="/">
    <div class="h-44 rounded-3xl border-4 border-black bg-white p-5 ">
      <div>
        <p class="text-2xl font-bold">My Title</p>
        <p class="mt-4 text-lg font-medium">Description</p>
      </div>
    </div>
  </a>
```

會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20230914/20162607SI334m6FYo.png](https://ithelp.ithome.com.tw/upload/images/20230914/20162607SI334m6FYo.png)

加入置中屬性，items-center 是垂直置中，要讓它產生作用，要跟 flex 一起宣告：

```html
<a href="/">
    <div class="h-44 rounded-3xl border-4 border-black bg-white p-5 flex items-center">
      <div>
        <p class="text-2xl font-bold">My Title</p>
        <p class="mt-4 text-lg font-medium">Description</p>
      </div>
    </div>
  </a>
```

會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20230914/201626079987TnmhOs.png](https://ithelp.ithome.com.tw/upload/images/20230914/201626079987TnmhOs.png)

最後加入當滑鼠移動到卡片上方時，會自動變背景顏色，要達到這個目的，必須要使用 hover:，表示滑鼠移動事件，後面可以加上任何屬性，在這裡的範例是加入背景顏色為黃色 hover:bg-yellow-200：

```html
<a href="/">
    <div class="h-44 rounded-3xl border-4 border-black bg-white p-5 flex items-center hover:bg-yellow-200">
      <div>
        <p class="text-2xl font-bold">My Title</p>
        <p class="mt-4 text-lg font-medium">Description</p>
      </div>
    </div>
  </a>
```

最後的結果會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20230914/20162607EVYmoB6ng4.png](https://ithelp.ithome.com.tw/upload/images/20230914/20162607EVYmoB6ng4.png)

[今日完整範例](https://play.tailwindcss.com/UhYPjLtA6G?layout=horizontal&size=1748x720)

**tailwindcss 從零開始學¹ - Day8 [完]**