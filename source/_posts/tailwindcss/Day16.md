---
title: tailwindcss 從零開始學¹ - Day16 - 表單輸入
date: 2023-09-23 08:57:48
tags:
---
這個單元要開始來討論表單的製作方式，最後呈現的樣子：

![https://ithelp.ithome.com.tw/upload/images/20230924/201626073sVyEPjEI4.png](https://ithelp.ithome.com.tw/upload/images/20230924/201626073sVyEPjEI4.png)

先宣告一個最基本的表單輸入框：

```html
<input class="f" type="text" placeholder="輸入 Email" />
```

加入文字屬性：

- text-sm：文字大小
- font-normal：文字字型
- text-gray-700：文字顏色

```html
<input class="text-sm font-normal text-gray-700" type="text" placeholder="輸入 Email" />
```

加入外框屬性：

- border：新增外框
- border-gray-300：外框顏色

```html
<input class="text-sm font-normal text-gray-700 border border-gray-300" type="text" placeholder="輸入 Email" />
```

加入間距屬性：

- px-3：水平間距
- py-3：垂直間距

```html
<input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3" type="text" placeholder="輸入 Email" />
```

加入圓角跟背景顏色：

- rounded-lg：圓角
- bg-white：背景顏色

```html
<input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3 rounded-lg bg-white" type="text" placeholder="輸入 Email" />
```

加入 placeholder 屬性，使用 placeholder: 後面帶入任何的顏色屬性，就可以改變 placeholder 的文字顏色：

- placeholder:text-gray-500：placeholder 文字顏色

```html
<input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3 rounded-lg bg-white placeholder:text-gray-500" type="text" placeholder="輸入 Email" />
```

當使用表單的文字輸入時，在網頁上按下鍵盤的 tab 鍵，可以將游標移轉到的表單之中，如果要讓表單產生變化，可以使用 focus:，後面一樣帶入想要的顏色，但這個屬性要跟 focus:outline-non 一起使用：

- focus:border-fuchsia-300：focus 顏色
- focus:outline-non：當 focus 時，取消原本外框

```html
<input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3 rounded-lg bg-white placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none" type="text" placeholder="輸入 Email" />
```

加入動畫屬性：

- transition-all：可以顯示當滑鼠指定這個表單輸入時，產生一個轉化動畫效果

```html
<input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3 rounded-lg bg-white placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none transition-all" type="text" placeholder="輸入 Email" />
```

最後表單通常都會加入一個文字描述，來說明這個輸入欄位：

```html
<div class="p-4">
  <label class="mb-2 font-bold text-gray-700">Email</label>
  <input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3 rounded-lg bg-white placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none transition-all" type="text" placeholder="輸入 Email" />
</div>
```

[今日完整範例](https://play.tailwindcss.com/DvC3TLfSHd?layout=horizontal&size=1244x720)

**tailwindcss 從零開始學¹ - Day16 [完]**