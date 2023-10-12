---
title: tailwindcss 從零開始學¹ - Day9 - 卡片排版組合
date: 2023-09-16 14:34:34
tags:
---
這個單元將接續上一個單元製作的卡片排版來延伸。

一般來說使用卡片排版，會有好幾個卡片同時出現，接下來就繼續討論如何放入多個卡片排版。

一開始宣告最上層的 div：

```html
<div class="container mx-auto mt-10">
</div>
```

這裡使用 container 的寬度，mx-auto 自動置中，mt-10 上方留白 10。

```html
<div class="container mx-auto mt-10">
  <div class="grid grid-cols-1 gap-4 lg:grid-cols-3">
  </div>
</div>
```

`grid grid-cols-1` 可以在水平方向切成一個單位，如果是 `grid grid-cols-3` 就可以在水平方向切成三個單位，加上 `gap-4` 表示單位與單位之間的間隔為 4。

所以 `grid grid-cols-1 lg:grid-cols-3` 就表示當寬度大於 lg 時會切成三個單位，小於 lg 會切成一個單位。

最後將上一個單位做成的卡片放入，一次放上三組：

```html
<div class="container mx-auto mt-10">
  <div class="grid grid-cols-1 gap-4 lg:grid-cols-3">
    <a href="/">
      <div class="flex h-44 w-full items-center rounded-3xl border-4 border-black bg-white p-5 shadow-[4px_4px_0_0_#000] hover:bg-yellow-200">
        <div>
          <p class="text-2xl font-bold">My Title</p>
          <p class="mt-4 text-lg font-medium leading-relaxed">Description</p>
        </div>
      </div>
    </a>
    <a href="/">
      <div class="flex h-44 w-full items-center rounded-3xl border-4 border-black bg-white p-5 shadow-[4px_4px_0_0_#000] hover:bg-yellow-200">
        <div>
          <p class="text-2xl font-bold">My Title</p>
          <p class="mt-4 text-lg font-medium leading-relaxed">Description</p>
        </div>
      </div>
    </a>
    <a href="/">
      <div class="flex h-44 w-full items-center rounded-3xl border-4 border-black bg-white p-5 shadow-[4px_4px_0_0_#000] hover:bg-yellow-200">
        <div>
          <p class="text-2xl font-bold">My Title</p>
          <p class="mt-4 text-lg font-medium leading-relaxed">Description</p>
        </div>
      </div>
    </a>
  </div>
</div>
```

開啟瀏覽器呈現的樣子：

![https://ithelp.ithome.com.tw/upload/images/20230916/20162607epszo9qdoU.png](https://ithelp.ithome.com.tw/upload/images/20230916/20162607epszo9qdoU.png)

本單位學習到新的標籤：

* grid：格子排版
* lg:grid-cols-3：版面大於 lg 則使用 grid-cols-3
* grid-cols-1：版面小於 lg 則使用使用 grid-cols-1

[今日完整範例](https://play.tailwindcss.com/fJ1Z5bD72h?layout=horizontal)

**tailwindcss 從零開始學¹ - Day9 [完]**
