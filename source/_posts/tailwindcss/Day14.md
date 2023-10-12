---
title: tailwindcss 從零開始學¹ - Day14 - Dashboard 排版
date: 2023-09-21 19:16:26
tags:
---
這個單元要來繼續完成 Dashboard 排版，上一個單元完成了以下的排版方式：

```html
<div class="flex h-screen">
  <div class="hidden w-80 bg-gray-800 sm:flex">
    <p class="text-white">Left</p>
  </div>
  
  <div class="w-full bg-slate-100">
    <h1>Right</h1>
  </div>
</div>
```

但這樣子的寫法在 RWD 無法起作用，會使得左側的排版消失，這也是 `hidden` 與 `sm:flex` 起作用的關係，所以直接宣告一個新的 `div` 標籤，來讓當寬度小於 sm 時，會出現一個 menu bar：

```html
<div class="flex h-screen">
  <div class="hidden w-80 bg-gray-800 sm:flex">
    <p class="text-white">Left</p>
  </div>
  
  <div class="">
  </div>
  
  <div class="w-full bg-slate-100">
    <h1>Right</h1>
  </div>
</div>
```

加入 `h-full` 高度滿版，`w-64` 寬度 64，`bg-gray-800` 背景顏色，`sm:hidden` 當寬度大於 sm 時會消失：

```html
<div class="flex h-screen">
  <div class="hidden w-80 bg-gray-800 sm:flex">
    <p class="text-white">Left</p>
  </div>
  
  <div class="absolute h-full w-64 bg-gray-800 sm:hidden">
  </div>
  
  <div class="w-full bg-slate-100">
    <h1>Right</h1>
  </div>
</div>
```

在這個 menu 的標籤內，加入兩個按鈕，一個開啟按鈕，另外一個關閉按鈕。

- `absolute`：使用相對位置。
- `right-0`：使用相對位置，靠右 0。
- `-mr-10`：使用相對位置，對右邊的 margin 間距為 -10，這裡如果加上一個負號，就表示使用相反的間距。
- `cursor-pointer`：出現滑鼠的超連結游標。

```html
<div class="flex h-screen">
  <div class="hidden w-80 bg-gray-800 sm:flex">
    <p class="text-white">Left</p>
  </div>
  
  <div class="absolute h-full w-64 bg-gray-800 sm:hidden">
    <button class="absolute right-0 -mr-10 mt-16 h-10 w-10 cursor-pointer rounded-br rounded-tr bg-gray-800 text-sm text-white">開啟</button>
    <button class="absolute right-0 -mr-10 mt-16 hidden h-10 w-10 cursor-pointer rounded-br rounded-tr bg-gray-800 text-sm text-white">關閉</button>
  </div>
  
  <div class="w-full bg-slate-100">
    <h1>Right</h1>
  </div>
</div>
```

在第二個按鈕加入 `hidden`，表示先隱藏起來。

接下來加入這個 menu 上面的文字，主要是確定 menu 的內容有顯示出來：

```html
<div class="flex h-screen">
  <div class="hidden w-80 bg-gray-800 sm:flex">
    <p class="text-white">Left</p>
  </div>
  
  <div class="absolute h-full w-64 bg-gray-800 sm:hidden">
    <button class="absolute right-0 -mr-10 mt-16 h-10 w-10 cursor-pointer rounded-br rounded-tr bg-gray-800 text-sm text-white">開啟</button>
    <button class="absolute right-0 -mr-10 mt-16 hidden h-10 w-10 cursor-pointer rounded-br rounded-tr bg-gray-800 text-sm text-white">關閉</button>
    
    <div class="px-4 py-6">
      <h1 class="px-2 text-xl text-gray-100">Title</h1>
    </div>
  </div>
  
  <div class="w-full bg-slate-100">
    <h1>Right</h1>
  </div>
</div>
```

那要如何讓按鈕產生作用？

使用 id 來針對 div 標籤產生名稱，所以加入了這些 id 來辨識 `id="mobile-nav"` 、  `id="openSideBar"` 、 `id="closeSideBar"`：

```html
<div class="flex h-screen">
  <div class="hidden w-80 bg-gray-800 sm:flex">
    <p class="text-white">Left</p>
  </div>
  
  <div class="absolute h-full w-64 bg-gray-800 sm:hidden" id="mobile-nav">
    <button id="openSideBar" class="absolute right-0 -mr-10 mt-16 h-10 w-10 cursor-pointer rounded-br rounded-tr bg-gray-800 text-sm text-white">開啟</button>
    <button id="closeSideBar" class="absolute right-0 -mr-10 mt-16 hidden h-10 w-10 cursor-pointer rounded-br rounded-tr bg-gray-800 text-sm text-white">關閉</button>
    
    <div class="px-4 py-6">
      <h1 class="px-2 text-xl text-gray-100">Title</h1>
    </div>
  </div>
  
  <div class="w-full bg-slate-100">
    <h1>Right</h1>
  </div>
</div>
```

最後加入按鈕的按下事件，`onclick` 事件，並且分別帶入函式名稱，`onclick="sidebarHandler(true)"` 表示當按鈕按下呼叫 sidebarHandler 這個函式，並且帶入參數為 true。

`onclick="sidebarHandler(false)"` 表示當按鈕按下呼叫 sidebarHandler 這個函式，並且帶入參數為 false。

```html
<div class="flex h-screen">
  <div class="hidden w-80 bg-gray-800 sm:flex">
    <p class="text-white">Left</p>
  </div>
  
  <div class="absolute  h-full w-64 bg-gray-800 sm:hidden" id="mobile-nav">
    <button id="openSideBar" class="absolute right-0 -mr-10 mt-16 h-10 w-10 cursor-pointer rounded-br rounded-tr bg-gray-800 text-sm text-white" onclick="sidebarHandler(true)">開啟</button>
    <button id="closeSideBar" class="absolute right-0 -mr-10 mt-16 hidden h-10 w-10 cursor-pointer rounded-br rounded-tr bg-gray-800 text-sm text-white" onclick="sidebarHandler(false)">關閉</button>
    
    <div class="px-4 py-6">
      <h1 class="px-2 text-xl text-gray-100">Title</h1>
    </div>
  </div>
  
  <div class="w-full bg-slate-100">
    <h1>Right</h1>
  </div>
</div>
```

然後加入以下 javascript 程式來產生作用：

```
<script>
  var sideBar = document.getElementById("mobile-nav"); //取得 id=mobile-nav 的標籤
  var openSidebar = document.getElementById("openSideBar"); //取得 id=openSideBar 的標籤
  var closeSidebar = document.getElementById("closeSideBar"); //取得 id=closeSideBar 的
  sideBar.style.transform = "translateX(-260px)"; //先讓 sideBar 的x軸位置在 -260

  function sidebarHandler(flag) {
    if (flag) {
      sideBar.style.transform = "translateX(0px)"; //改變 sideBar 的x軸位置在 0
      openSidebar.classList.add("hidden"); //加入 openSidebar 一個 hidden 屬性
      closeSidebar.classList.remove("hidden"); //移除 closeSidebar 的 hidden 屬性
    } else {
      sideBar.style.transform = "translateX(-260px)";
      closeSidebar.classList.add("hidden");
      openSidebar.classList.remove("hidden");
    }
  }
</script>
```

所以當畫面寬度小於 sm 時，會顯示這樣：

![https://ithelp.ithome.com.tw/upload/images/20230921/20162607Kxy0gpKOhY.png](https://ithelp.ithome.com.tw/upload/images/20230921/20162607Kxy0gpKOhY.png)

按下開啟按鈕後，會顯示這樣：

![https://ithelp.ithome.com.tw/upload/images/20230921/20162607lPvoFU7Vtt.png](https://ithelp.ithome.com.tw/upload/images/20230921/20162607lPvoFU7Vtt.png)

這樣就完成這個 Dashboard 的簡單排版了。

[今日完整範例](https://play.tailwindcss.com/Liywc6vT0Z?layout=horizontal&size=546x720)

**tailwindcss 從零開始學¹ - Day14 [完]**