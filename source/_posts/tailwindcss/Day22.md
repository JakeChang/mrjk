---
title: tailwindcss 從零開始學¹ - Day22 - 登入畫面
date: 2023-09-29 09:21:56
tags:
---
這個單元來實作登入畫面這個單元來實作登入畫面，最後希望完成的畫面如：

![https://ithelp.ithome.com.tw/upload/images/20230929/201626079pDqX7NYzI.png](https://ithelp.ithome.com.tw/upload/images/20230929/201626079pDqX7NYzI.png)

首先一開始宣告整個架構的 div 標籤：

```html
<div>
  <div>Admin</div>
  <div>登入</div>
  
  <form>
    <div>
      <div>
        <input type="email" placeholder="帳號" />
      </div>
      <div>
        <input type="password" placeholder="密碼" />
      </div>
    </div>

    <div>
      <button type="submit">
        登入
      </button>
    </div>
  </form>
</div>
```

這個架構從標題到輸入框，最後用一個按鈕收尾。而在輸入框跟按鈕在之前的討論都有討論到，可以參考 [Day4 - 一個簡單的按鈕](https://ithelp.ithome.com.tw/articles/10316799) 與 [Day16 - 表單輸入](https://ithelp.ithome.com.tw/articles/10325577)。

這邊就直接加入按鈕與輸入框的樣式：

```html
<div>
  <div>Admin</div>
  <div>登入</div>
  
  <form>
    <div>
      <div>
        <input type="email" autocomplete="email" required class="relative block w-full appearance-none rounded-none rounded-t-md border border-gray-300 px-3 py-3 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-blue-500 focus:outline-none focus:ring-1 focus:ring-blue-500 sm:text-sm" placeholder="帳號" />
        </div>
        <div>
          <input type="password" autocomplete="current-password" required class="relative block w-full appearance-none rounded-none rounded-b-md border border-gray-300 px-3 py-3 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-blue-500 focus:outline-none focus:ring-1 focus:ring-blue-500 sm:text-sm" placeholder="密碼" />
        </div>
    </div>

    <div>
      <button type="submit" class="relative flex w-full justify-center rounded-md border border-transparent bg-blue-600 py-3 text-sm font-medium text-white hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 disabled:bg-blue-400">
        登入
      </button>
    </div>
  </form>
</div>
```

呈現畫面如：

![https://ithelp.ithome.com.tw/upload/images/20230929/20162607sYUYbfKaU1.png](https://ithelp.ithome.com.tw/upload/images/20230929/20162607sYUYbfKaU1.png)

接下來加入置中跟寬度的樣式：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <div class="w-full max-w-md">
    <div>Admin</div>
    <div>登入</div>
  
    <form>
      <div>
        <div>
          <input type="email" autocomplete="email" required class="relative block w-full appearance-none rounded-none rounded-t-md border border-gray-300 px-3 py-3 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-blue-500 focus:outline-none focus:ring-1 focus:ring-blue-500 sm:text-sm" placeholder="帳號" />
          </div>
          <div>
            <input type="password" autocomplete="current-password" required class="relative block w-full appearance-none rounded-none rounded-b-md border border-gray-300 px-3 py-3 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-blue-500 focus:outline-none focus:ring-1 focus:ring-blue-500 sm:text-sm" placeholder="密碼" />
          </div>
      </div>

      <div>
        <button type="submit" class="relative flex w-full justify-center rounded-md border border-transparent bg-blue-600 py-3 text-sm font-medium text-white hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 disabled:bg-blue-400">
        登入
        </button>
      </div>
    </form>
  </div>
</div>
```

這裡多加了一個 div 標籤樣式，`w-full` 與 `max-w-md`，表示在最大寬度為 `w-full` 時，使用寬度為 `max-w-md`。呈現畫面如：

![https://ithelp.ithome.com.tw/upload/images/20230929/20162607lKWF0F4hSe.png](https://ithelp.ithome.com.tw/upload/images/20230929/20162607lKWF0F4hSe.png)

接下來針對文字與表單增加樣式：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <div class="w-full max-w-md">
    <div class="text-center text-3xl font-extrabold text-gray-900">Admin</div>
    <div>
      <h2 class="mt-6 text-center text-2xl text-gray-900">登入</h2>
    </div>
  
    <form class="mt-8 space-y-6" @submit.prevent="signin">
      <div>
        <div>
          <input type="email" autocomplete="email" required class="relative block w-full appearance-none rounded-none rounded-t-md border border-gray-300 px-3 py-3 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-blue-500 focus:outline-none focus:ring-1 focus:ring-blue-500 sm:text-sm" placeholder="帳號" />
          </div>
          <div>
            <input type="password" autocomplete="current-password" required class="relative block w-full appearance-none rounded-none rounded-b-md border border-gray-300 px-3 py-3 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-blue-500 focus:outline-none focus:ring-1 focus:ring-blue-500 sm:text-sm" placeholder="密碼" />
          </div>
      </div>

      <div>
        <button type="submit" class="relative flex w-full justify-center rounded-md border border-transparent bg-blue-600 py-3 text-sm font-medium text-white hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 disabled:bg-blue-400">
        登入
        </button>
      </div>
    </form>
  </div>
</div>
```

在這可以發現我用了兩種不一樣的文字樣式，一種是沒有 `<h2>`，另外一種是加入 `<h2>`，兩種寫法都大同小異。

然後在表單內加入了 `@submit.prevent="signin"`，表示防止按下按鈕會直接整頁換頁。

目前樣式會呈現這樣，但發現兩個 input 之間的現會太粗：

![https://ithelp.ithome.com.tw/upload/images/20230929/201626075fdVjcNyEh.png](https://ithelp.ithome.com.tw/upload/images/20230929/201626075fdVjcNyEh.png)

這裡用到的技巧就是使用負號的位置調整，`-space-y-px` 表示針對 y 軸上方移動 1px：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <div class="w-full max-w-md">
    <div class="text-center text-3xl font-extrabold text-gray-900">Admin</div>
    <div>
      <h2 class="mt-6 text-center text-2xl text-gray-900">登入</h2>
    </div>
  
    <form class="mt-8 space-y-6" @submit.prevent="signin">
      <div class="-space-y-px rounded-md shadow-sm">
        <div>
          <input type="email" autocomplete="email" required class="relative block w-full appearance-none rounded-none rounded-t-md border border-gray-300 px-3 py-3 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-blue-500 focus:outline-none focus:ring-1 focus:ring-blue-500 sm:text-sm" placeholder="帳號" />
          </div>
          <div>
            <input type="password" autocomplete="current-password" required class="relative block w-full appearance-none rounded-none rounded-b-md border border-gray-300 px-3 py-3 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-blue-500 focus:outline-none focus:ring-1 focus:ring-blue-500 sm:text-sm" placeholder="密碼" />
          </div>
      </div>

      <div>
        <button type="submit" class="relative flex w-full justify-center rounded-md border border-transparent bg-blue-600 py-3 text-sm font-medium text-white hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 disabled:bg-blue-400">
        登入
        </button>
      </div>
    </form>
  </div>
</div>
```

最後在按鈕內放入一個轉圈圈動畫，當然這個動畫會配合前端如 Vue3 一起整合，一開始不會顯示轉圈圈，按下之後才會顯示轉圈圈：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <div class="w-full max-w-md">
    <div class="text-center text-3xl font-extrabold text-gray-900">Admin</div>
    <div>
      <h2 class="mt-6 text-center text-2xl text-gray-900">登入</h2>
    </div>
    <form class="mt-8 space-y-6" @submit.prevent="signin">
      <div class="-space-y-px rounded-md shadow-sm">
        <div>
          <input type="email" autocomplete="email" required class="relative block w-full appearance-none rounded-none rounded-t-md border border-gray-300 px-3 py-3 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-blue-500 focus:outline-none focus:ring-1 focus:ring-blue-500 sm:text-sm" placeholder="帳號" />
        </div>
        <div>
          <input type="password" autocomplete="current-password" required class="relative block w-full appearance-none rounded-none rounded-b-md border border-gray-300 px-3 py-3 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-blue-500 focus:outline-none focus:ring-1 focus:ring-blue-500 sm:text-sm" placeholder="密碼" />
        </div>
      </div>

      <div>
        <button type="submit" class="relative flex w-full justify-center rounded-md border border-transparent bg-blue-600 py-3 text-sm font-medium text-white hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 disabled:bg-blue-400">
          <span>
            <svg class="-ml-1 mr-3 h-5 w-5 animate-spin text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
              <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
              <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
            </svg>
          </span>
          登入
        </button>
      </div>
    </form>
  </div>
</div>
```

完成的畫面如：

![https://ithelp.ithome.com.tw/upload/images/20230929/201626079pDqX7NYzI.png](https://ithelp.ithome.com.tw/upload/images/20230929/201626079pDqX7NYzI.png)

[今日完整範例](https://play.tailwindcss.com/9QjWsqPTU3)

**tailwindcss 從零開始學¹ - Day22 [完]**
