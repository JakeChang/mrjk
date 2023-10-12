---
title: tailwindcss 從零開始學¹ - Day24 - 表單 input 進階
date: 2023-10-01 14:51:29
tags:
---
這個單元來討論一些關於表單 input 的一些進階用法。

回到 [tailwindcss - 從零開始學 - Day16](https://ithelp.ithome.com.tw/articles/10325577) 直接使用其最後的完整表單 input 樣式：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3 rounded-lg bg-white placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none transition-all" type="text" placeholder="輸入 Email" />
</div>
```

如果要讓這個表單 input 欄位設定為必填欄位，可以使用 `required`，並且加入 `required:` 樣式：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3 rounded-lg bg-white placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none transition-all required:border-red-600" type="text" placeholder="輸入 Email" required />
</div>
```

這邊加入了 `required:` 樣式，後面接上 `border` 的框線顏色 `required:border-red-600`。

如果要讓這個表單 input 欄位設定錯誤訊息樣式，可以使用 `invalid:` 樣式：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3 rounded-lg bg-white placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none transition-all invalid:border-red-600" type="text" placeholder="輸入 Email" required />
</div>
```

這邊加入了 `invalid:` 樣式，後面接上 `border` 的框線顏色 `invalid:border-red-600`。

如果要讓這個表單 input 欄位設定無法使用，可以使用 `disabled`，並且加入 `disabled:` 樣式：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3 rounded-lg bg-white placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none transition-all disabled:border-gray-100" type="text" placeholder="輸入 Email" disabled />
</div>
```

這邊加入了 `disabled:` 樣式，後面接上 `border` 的框線顏色 `disabled:border-gray-100`。

最後也可以針對 placeholder 進行樣式修改，使用 `placeholder:`：

```html
<div class="flex min-h-screen w-screen items-center justify-center">
  <input class="text-sm font-normal text-gray-700 border border-gray-300 px-3 py-3 rounded-lg bg-white focus:border-fuchsia-300 focus:outline-none transition-all placeholder:italic placeholder:text-slate-400" type="text" placeholder="輸入 Email" />
</div>
```

這邊加入了 `placeholder:` 樣式，後面接上文字顏色 `placeholder:text-slate-400` 與斜體樣式 `placeholder:italic`。

[今日完整範例](https://play.tailwindcss.com/fIKpYwOuil)

**tailwindcss 從零開始學¹ - Day24 [完]**