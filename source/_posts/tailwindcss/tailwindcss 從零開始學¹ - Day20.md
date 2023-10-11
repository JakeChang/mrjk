---
title: tailwindcss 從零開始學¹ - Day20 - Table
date: 2023-09-27 13:38:28
tags:
---
這個單元要來介紹表格的基本做法，首先，先宣告一個最基本的表格：

```html
<table>
  <thead>
    <tr>
      <th>Col</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td></td>
    </tr>
  </tbody>
</table>
```

先針對 `thead` 增加樣式：

```html
<table>
  <thead>
    <tr>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-left align-middle font-bold uppercase text-slate-400 opacity-70">Col</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td></td>
    </tr>
  </tbody>
</table>
```

樣式說明：

- text-xxs：文字大小
- border-b：底部增加框線
- border-gray-200：框線顏色
- bg-transparent：背景透明
- px-6：水平方向間隔
- py-3：垂直方向間隔
- text-left：文字靠左邊
- align-middle：垂直置中
- font-bold：文字粗體
- uppercase：英文大寫
- text-slate-400：文字顏色
- opacity-70：透明度

接下來針對 `tbody` 新增樣式：

```html
<table>
  <thead>
    <tr>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-left align-middle font-bold uppercase text-slate-400 opacity-70">Col</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="border-b bg-transparent p-2"></td>
    </tr>
  </tbody>
</table>
```

樣式說明：

- border-b：底部增加框線
- bg-transparent：背景透明
- p-2：所有方向的間隔

接下來針對 `table` 新增樣式：

```html
<table class="w-full border-gray-200 text-slate-500">
  <thead>
    <tr>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-left align-middle font-bold uppercase text-slate-400 opacity-70">Col</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="border-b bg-transparent p-2"></td>
    </tr>
  </tbody>
</table>
```

樣式說明：

- w-full：讓整個 table 呈現滿版
- border-gray-200：框線顏色
- text-slate-500：文字顏色

這邊要注意的是雖然已經在 `table` 新增文字顏色的樣式，但如果在 `td` 也有新增文字顏色的樣式，則會以 `td` 的樣式為主。

因為目前只有一行，所以這邊另外新增另外三行：

```html
<table class="w-full border-gray-200 text-slate-500">
  <thead>
    <tr>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-left align-middle font-bold uppercase text-slate-400 opacity-70">Col1</th>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col2</th>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col3</th>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="border-b bg-transparent p-2"></td>
      <td class="border-b bg-transparent p-2 text-center align-middle"></td>
      <td class="border-b bg-transparent p-2 text-center align-middle"></td>
      <td class="border-b bg-transparent p-2 text-center align-middle text-sm"></td>
    </tr>
  </tbody>
</table>
```

接下來針對表格內放置圖片：

```html
<table class="w-full border-gray-200 text-slate-500">
  <thead>
    <tr>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-left align-middle font-bold uppercase text-slate-400 opacity-70">Col1</th>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col2</th>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col3</th>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="border-b bg-transparent p-2">
        <div class="flex flex-row px-2 py-1">
          <div class="mr-4">
            <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" class="h-9 w-9 rounded-xl" />
          </div>
          <div class="flex flex-col">
            <h6 class="mb-0 text-sm hover:text-red-600">aaa</h6>
            <p class="mb-0 text-xs leading-tight text-slate-400">aaa</p>
          </div>
        </div>
      </td>
      <td class="border-b bg-transparent p-2 text-center align-middle"></td>
      <td class="border-b bg-transparent p-2 text-center align-middle"></td>
      <td class="border-b bg-transparent p-2 text-center align-middle text-sm"></td>
    </tr>
  </tbody>
</table>
```

所以目前會得到這個效果，圖片有根據所設定的大小並切成圓角，然後圖片旁邊放上兩組文字：

![https://ithelp.ithome.com.tw/upload/images/20230927/20162607MC8tQ0zD64.png](https://ithelp.ithome.com.tw/upload/images/20230927/20162607MC8tQ0zD64.png)

然後再另外兩個表個 `td` 也加入文字：

```html
<table class="w-full border-gray-200 text-slate-500">
  <thead>
    <tr>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-left align-middle font-bold uppercase text-slate-400 opacity-70">Col1</th>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col2</th>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col3</th>
      <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="border-b bg-transparent p-2">
        <div class="flex flex-row px-2 py-1">
          <div class="mr-4">
            <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" class="h-9 w-9 rounded-xl" />
          </div>
          <div class="flex flex-col">
            <h6 class="mb-0 text-sm hover:text-red-600">aaa</h6>
            <p class="mb-0 text-xs leading-tight text-slate-400">aaa</p>
          </div>
        </div>
      </td>
      <td class="border-b bg-transparent p-2 text-center align-middle">
        <p class="mb-0 text-xs font-semibold">sub title</p>
      </td>
      <td class="border-b bg-transparent p-2 text-center align-middle">
        <p class="mb-0 text-xs font-semibold">item 1</p>
        <p class="mb-0 text-xs text-slate-400">item 2</p>
      </td>
      <td class="border-b bg-transparent p-2 text-center align-middle text-sm"></td>
    </tr>
  </tbody>
</table>
```

所以目前會呈現這個效果：

![https://ithelp.ithome.com.tw/upload/images/20230927/20162607YOSr8V4JHo.png](https://ithelp.ithome.com.tw/upload/images/20230927/20162607YOSr8V4JHo.png)

在最後的表格加入一個 tag 的顯示方式：

```html
<div class="p-0">
  <table class="w-full border-gray-200 text-slate-500">
    <thead>
      <tr>
        <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-left align-middle font-bold uppercase text-slate-400 opacity-70">Col1</th>
        <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col2</th>
        <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col3</th>
        <th class="text-xxs border-b border-gray-200 bg-transparent px-6 py-3 text-center align-middle font-bold uppercase text-slate-400 opacity-70">Col4</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="border-b bg-transparent p-2">
          <div class="flex flex-row px-2 py-1">
            <div class="mr-4">
              <img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" class="h-9 w-9 rounded-xl" />
            </div>
            <div class="flex flex-col">
              <h6 class="mb-0 text-sm hover:text-red-600">aaa</h6>
              <p class="mb-0 text-xs leading-tight text-slate-400">aaa</p>
            </div>
          </div>
        </td>
        <td class="border-b bg-transparent p-2 text-center align-middle">
          <p class="mb-0 text-xs font-semibold">sub title</p>
        </td>
        <td class="border-b bg-transparent p-2 text-center align-middle">
          <p class="mb-0 text-xs font-semibold">item 1</p>
          <p class="mb-0 text-xs text-slate-400">item 2</p>
        </td>
        <td class="border-b bg-transparent p-2 text-center align-middle text-sm">
          <span class="rounded-lg bg-gradient-to-tl from-green-600 to-lime-400 px-2 py-1 text-center align-baseline text-xs font-bold uppercase text-white">TAG</span>
        </td>
      </tr>
    </tbody>
  </table>
</div>
```

最後的呈現效果：

![https://ithelp.ithome.com.tw/upload/images/20230927/20162607VCS7YdHWnC.png](https://ithelp.ithome.com.tw/upload/images/20230927/20162607VCS7YdHWnC.png)

[今日完整範例](https://play.tailwindcss.com/O7HPhaBPmI?size=1206x720)

**tailwindcss 從零開始學¹ - Day20 [完]**
