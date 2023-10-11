---
title: tailwindcss 從零開始學¹ - Day1 - 為何而戰
date: 2023-09-08 10:57:59
tags:
---
### 前言

前端網頁開發至今發展 20 餘年，在 2023 年的今日如果還是想要從事網頁開發，到底該從何下手呢？還是一樣從 HTML、CSS 與 JavaScript 開始嗎？當然不可否認這三個技術的重要性，因為現今所有的框架也都是基於它們之上，也包括這個系列要介紹的 tailwindcss。

如果想要徹底學習與了解網頁開發，那我會建議你，還是要把 HTML、CSS 與 JavaScript 的基礎學好，對於整體的網頁開發才會有更深入的了解。但如果是工作上需要且沒有太多時間怎麼辦，總不可能從頭開始學吧。

那找到一個合適的框架來製作是最有效率的方法，tailwindcss 就是一個可以快速搭建出網頁排版的 CSS 框架。

這個系列你將會學到如何使用 tailwindcss 來建構出網頁，我將從最基本的概念講起，你不需要學會 HTML 與 CSS 才能學 tailwindcss，畢竟我們的目的是幫助工作上的需求，快速有效率是整個開發的核心思想。

tailwindcss 是一個簡單且易學的框架，只要有瞭解基本的 HTML 語法就可以開始了。

### Bootstrap 與 tailwindcss

tailwindcss 是一個 CSS 框架，而這個框架跟 Bootstrap 有什麼差別，Bootstrap 用得好好的，我們還需要一個新的 CSS 框架嗎？直接來比較兩者的使用差別。

如果要使用 Bootstrap 來製作一個按鈕，會直接寫：

```html
<button type="button" class="btn btn-primary">Primary</button>
```

那如果改用 tailwindcss ，要製作一個按鈕時，會發現官方並沒有提供按鈕的元件來直接使用，而是任意由自己來定義，所以如果使用 tailwindcss 來製作按鈕時，可能會這樣寫：

```html
<a class="rounded border border-black bg-blue-500 px-12 py-3 text-lg text-white hover:bg-transparent hover:text-indigo-600" href="/">Button</a>
```

兩者的差別顯而易見，tailwindcss 用了許多類別才能製作一個按鈕，而 Bootstrap 只需要兩個 class 就搞定了，但不要因此就說 Bootstrap 比 tailwindcss 好用且簡單，事情並不是表面上看到的這個樣子。

先來看看 Bootstrap 的原始檔案是如何定義 btn 這個類別的：

```css
.btn {
  --bs-btn-padding-x: 0.75rem;
  --bs-btn-padding-y: 0.375rem;
  --bs-btn-font-family: ;
  /* ...省略 */
  display: inline-block;
  padding: var(--bs-btn-padding-y) var(--bs-btn-padding-x);
  font-family: var(--bs-btn-font-family);
  font-size: var(--bs-btn-font-size);
  font-weight: var(--bs-btn-font-weight);
  line-height: var(--bs-btn-line-height);
  /* ...省略 */
}
```

會發現 Bootstrap 直接把一個按鈕的樣式通通定義在 btn 裏面，好處是使用方便，直接兩個類別就可以引用到 HTML 檔案，但缺點是修改不易，如果只是想要修改字形的大小也是非常不容易的。

那麼 tailwindcss 在製作按鈕上，用了許多類別，直接觀看原始的 CSS 檔案：

```css
.rounded {
  border-radius: 0.25rem;
}

.border {
  border-width: 1px;
}

.px-12 {
  padding-left: 3rem;
  padding-right: 3rem;
}
```

會發現在 tailwindcss 上每一種 class 就專心定義一件事情而已，如圓角就定義圓角，寬度就定義寬度，而且可以直接從命名上清楚知道該 class 大概會是什麼樣式。反觀 Bootstrap，卻無法知道 btn 這個 class 的詳細定義，只能知道它是按鈕元件。

所以 tailwindcss 才又稱為 utility-first CSS 框架，功能優先的 CSS 框架，也就是一個 class 只負責單一性的樣式呈現，看到名稱就可以知道效果，而 Bootstrap 又稱為 components 框架，元件框架。

### 如何選擇這兩個框架

tailwindcss 框架，使用彈性大較大，在開發上比較可以做出自己想要的樣式卻又不想修改 CSS 的專案。而 Bootstrap 如果要做出想要的樣式就必須要修改 CSS，開發上並沒有比較省時間，而如果都用其提供好的元件，確實適合需要快速開發的專案。

如果專案上只需要建構出資訊網站、或內部使用的網站，那麼 Bootstrap 可能又會更適合一些，畢竟不用執著在一些細部的 UI 調整。

如果專案是開發出產品，是一個 Saas 服務或者平台，那麼我會建議使用 tailwindcss ，一來彈性大、修改容易，也可以快速搭建出一個雛形出來，若是背後有設計師希望達到的 UI 效果，那麼選擇 tailwindcss 準不會錯。

### 關於鐵人賽

最後，前端開發不會只有網頁排版的事情，會需要使用一個前端的開發框架，這裡推薦使用 Vue3.js，這裡可以去參考我的另外一個挑戰：

[Vue3 - 從零開始學](https://ithelp.ithome.com.tw/users/20162607/ironman/6461)

**tailwindcss 從零開始學¹ - Day1 [完]**