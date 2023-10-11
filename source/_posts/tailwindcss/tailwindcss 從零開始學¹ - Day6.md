---
title: tailwindcss 從零開始學¹ - Day6 - header RWD
date: 2023-09-13 19:03:20
tags:
---
這個單元會延續上一個單元來繼續製作，在上一個單元完成了一個非常簡單的 header 呈現方式，但還少了非常重要的 RWD 排版：

```html
<header class="bg-gray-800 text-white">
  <div class="px-6 py-3 flex flex-row justify-between container mx-auto">
    <div>
      <a href="#" class="text-xl font-medium">Logo</a>
    </div>
    <div>
      <a class="rounded border border-black bg-blue-500 px-12 py-3 text-lg text-white hover:bg-transparent hover:text-indigo-600" href="/">Button</a>
      <a class="rounded border border-black bg-blue-500 px-12 py-3 text-lg text-white hover:bg-transparent hover:text-indigo-600" href="/">Button</a>
      <a class="rounded border border-black bg-blue-500 px-12 py-3 text-lg text-white hover:bg-transparent hover:text-indigo-600" href="/">Button</a>
    </div>
  </div>
</header>
```

將瀏覽器寬度縮小時，排版會亂掉：

![https://ithelp.ithome.com.tw/upload/images/20230913/20162607NxT72ZT6ZC.png](https://ithelp.ithome.com.tw/upload/images/20230913/20162607NxT72ZT6ZC.png)

所以要製作支援 RWD 的排版，先試著排出當寬度縮小時，想要的排版。在這個範例裡，會希望較小螢幕的排版，會把右側的按鈕往下縮排，那麼就要使用垂直排版，將 `flex flex-row` 換成 `flex flex-col` 就會變成垂直排版：

```html
<header class="...">
  <div class="... flex flex-col ...">
    <div>
      <a href="#" class="...">Logo</a>
    </div>
    <div>
      <a class="..." href="/">Button</a>
      <a class="..." href="/">Button</a>
      <a class="..." href="/">Button</a>
    </div>
  </div>
</header>
```

在這裡把部分的 class name 沒有修改到的使用 ... 來取代，以節省說明。

但這樣修改後畫面將會變成：

![https://ithelp.ithome.com.tw/upload/images/20230913/20162607OZG4nYLtb2.png](https://ithelp.ithome.com.tw/upload/images/20230913/20162607OZG4nYLtb2.png)

此外，也會希望這三個按鈕呈現垂直排版，也一併加入 `flex flex-col`：

```html
<header class="...">
  <div class="...">
    <div>
      <a href="#" class="...">Logo</a>
    </div>
    <div class="flex flex-col">
      <a class="..." href="/">Button</a>
      <a class="..." href="/">Button</a>
      <a class="..." href="/">Button</a>
    </div>
  </div>
</header>
```

但這樣的修改並沒有辦法支援 RWD 排版，必須要在螢幕寬度較寬時，會使用水平排版，而在螢幕寬度變小時，會使用垂直排版。

在這裡就必須要了解 tailwindcss 的 5 種寬度設定：

* sm：640px
* md：768px
* lg：1024px
* xl：1280px
* 2xl：1536px
    
所以把原本的寫法：

```html
<div class="flex flex-col">
...
</div>
```

修改成：

```html
<div class="flex flex-col sm:flex-row">
...
</div>
```

`sm:flex-row` 這種寫法就表示當寬度小於 640px 時，會使用 `flex-row`。

又因為這行有寫另外一個水平排版 `flex-col`，所以這個表示意思就是當寬度小於 640px 時，會使用 `flex-col`，否則會使用 `flex-row`。

所以修改後：

```html
<header class="...">
  <div class="... flex flex-col sm:flex-row ...">
    <div>
      <a href="#" class="...">Logo</a>
    </div>
    <div class="flex flex-col sm:flex-row">
      <a class="..." href="/">Button</a>
      <a class="..." href="/">Button</a>
      <a class="..." href="/">Button</a>
    </div>
  </div>
</header>
```

如此一來，就可以支援當畫面小於 sm，也就是 640px，與大於 640px 的排版支援了。

最後補上一些 padding 的文字置中的整理，完整 html 為：

```html
<header class="bg-gray-800 text-white">
  <div class="container mx-auto flex flex-col justify-between px-6 py-3 text-center sm:flex-row">
    <div class="py-3">
      <a href="#" class="text-xl font-medium">Logo</a>
    </div>
    <div class="flex flex-col sm:flex-row">
      <a class="rounded border border-black bg-blue-500 px-12 py-3 text-lg text-white hover:bg-transparent hover:text-indigo-600" href="/">Button</a>
      <a class="rounded border border-black bg-blue-500 px-12 py-3 text-lg text-white hover:bg-transparent hover:text-indigo-600" href="/">Button</a>
      <a class="rounded border border-black bg-blue-500 px-12 py-3 text-lg text-white hover:bg-transparent hover:text-indigo-600" href="/">Button</a>
    </div>
  </div>
</header>
```

[今日完整範例](https://play.tailwindcss.com/idYAw7oLh7?layout=horizontal&size=234x720)

**tailwindcss 從零開始學¹ - Day6 [完]**