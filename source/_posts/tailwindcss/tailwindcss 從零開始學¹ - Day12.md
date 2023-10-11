---
title: tailwindcss 從零開始學¹ - Day12 - 卡片排版
date: 2023-09-19 18:32:01
tags:
---
這個單元將繼續使用 `relative` 與 `absolute` 來製作另外一種卡片排版。這是完整的樣子：

![https://ithelp.ithome.com.tw/upload/images/20230919/20162607JXu72dph1a.png](https://ithelp.ithome.com.tw/upload/images/20230919/20162607JXu72dph1a.png)

一開始宣告 `div` 標籤：

```html
<div class="">
  <p class="">Title</p>
  <p class="">sub title</p>

  <div class="">Circle</div>
</div>
```

加入屬性：

```html
<div class="mx-auto mt-10 w-1/3 rounded-lg bg-slate-50 p-4 shadow-lg">
  <p class="text-lg font-bold">Title</p>
  <p class="pt-1 text-sm">sub title</p>

  <div class="">Circle</div>
</div>
```

相關屬性說明，這些屬性之前都有講解到，這邊就不多做說明：

- `text-lg` `text-sm` `font-bold`：文字屬性
- `mt-10` `p-4` `pt-1`：邊界屬性
- `w-1/3`：寬度屬性
- `rounded-lg`：圓角屬性
- `bg-slate-50`：背景屬性
- `shadow-lg`：陰影屬性
- `mx-auto`：置中

會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20230919/20162607KnjLJwWm7T.png](https://ithelp.ithome.com.tw/upload/images/20230919/20162607KnjLJwWm7T.png)

在下方的 Circle，因為想要製作圓形的樣子，所以新增以下屬性：

```html
<div class="mx-auto mt-10 w-1/3 rounded-lg bg-slate-50 p-4 shadow-lg">
  <p class="text-lg font-bold">Title</p>
  <p class="pt-1 text-sm">sub title</p>

  <div class="h-24 w-24 flex items-center justify-center rounded-full bg-blue-300 shadow-lg">Circle</div>
</div>
```

比較特別的是 `rounded-full` 可以讓一個正方形的形狀切割成圓形，其它相關屬性說明：

- `h-24`：高度屬性
- `w-24`：寬度屬性
- `flex` `items-center` `justify-center`：置中
- `rounded-full`：完整圓角屬性
- `bg-blue-300`：背景屬性
- `shadow-lg`：陰影屬性

最後在上層加入 `relative` ，圓形加入 `absolute`，就可以讓圓形產生相對位置，並且位置設定為 `right-8` `top-10`，表示靠右邊 8，靠上方 10。

```html
<div class="relative mx-auto mt-10 w-1/3 rounded-lg bg-slate-50 p-4 shadow-lg">
  <p class="text-lg font-bold">Title</p>
  <p class="pt-1 text-sm">sub title</p>

  <div class="absolute right-8 top-10 h-24 w-24 flex items-center justify-center rounded-full bg-blue-300 shadow-lg">Circle</div>
</div>
```

最後的呈現結果：

![https://ithelp.ithome.com.tw/upload/images/20230919/20162607JXu72dph1a.png](https://ithelp.ithome.com.tw/upload/images/20230919/20162607JXu72dph1a.png)

[今日完整範例](https://play.tailwindcss.com/WAua3nDXye?layout=horizontal&size=1642x720)

**tailwindcss 從零開始學¹ - Day12 [完]**