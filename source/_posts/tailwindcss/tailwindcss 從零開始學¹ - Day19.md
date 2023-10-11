---
title: tailwindcss 從零開始學¹ - Day19 - 表單全
date: 2023-09-26 09:38:58
tags:
---
前面兩個單元討論了如何建構出表單內的欄位，但目前只有討論到 input 與 checkbox，這個單元將會討論所有欄位的寫法。

在 [Day16](https://ithelp.ithome.com.tw/articles/10325577) 討論過的 `input`：

```html
<div class="px-8 pb-2">
  <label class="mb-2 block font-bold text-gray-700">Email</label>
  <input class="w-full rounded-lg border border-gray-300 bg-white px-3 py-3 text-sm font-normal text-gray-700 transition-all placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none" type="text" placeholder="輸入 Email" />
</div>
```

`select` 下拉式選單：

```html
<div class="px-8 pb-2">
  <label class="mb-2 block font-bold text-gray-700">下下拉式選單</label>
  <select class="w-full appearance-none rounded-lg border border-gray-300 bg-white px-3 py-3 text-sm font-normal text-gray-700 transition-all placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none">
    <option value="false">否</option>
    <option value="true">是</option>
  </select>
</div>
```

一樣使用 `appearance-none` 消除原本的樣式。

`input file` 檔案選取：

```html
<div class="px-8 pb-2">
  <label class="mb-2 block font-bold text-gray-700">檔案選取</label>
  <input class="w-full appearance-none rounded-lg border border-gray-300 bg-white px-3 py-3 text-sm font-normal text-gray-700 transition-all placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none" type="file" accept=".png" />
</div>
```

在這裡跟下拉式選單使用一樣的樣式。

在 [Day18](https://ithelp.ithome.com.tw/articles/10327167) 討論過的 `checkbox`：

```html
<div class="px-8 pb-2 flex flex-row gap-6">
  <div>
    <label class="mb-2 font-bold text-gray-700">AAA</label>
    <input type="checkbox" class="relative float-left mr-2 mt-1 h-5 w-5 cursor-pointer appearance-none border border-slate-900 bg-white checked:border-0 checked:bg-gradient-to-tl checked:from-gray-100 checked:to-slate-800" />
  </div>
  <div>
    <label class="mb-2 font-bold text-gray-700">BBB</label>
    <input type="checkbox" class="relative float-left mr-2 mt-1 h-5 w-5 cursor-pointer appearance-none border border-slate-900 bg-white checked:border-0 checked:bg-gradient-to-tl checked:from-gray-100 checked:to-slate-800" />
  </div>
</div>
```

最後，可以編輯多行的 `textarea`：

```html
<div class="px-8 pb-2">
  <label class="mb-2 block font-bold text-gray-700" for="photo">Notes:</label>
  <textarea rows="5" class="block h-auto w-full appearance-none rounded-lg border border-gray-300 bg-white px-3 py-2 text-sm font-normal text-gray-700 transition-all placeholder:text-gray-500 focus:border-fuchsia-300 focus:outline-none" placeholder="Notes"></textarea>
</div>
```

這裡介紹的樣式大部分都使用一樣的樣式來顯示，說明了只要了解其中一個做法，其它欄位就相對簡單多了。

[今日完整範例](https://play.tailwindcss.com/zLzoInR47Z?layout=horizontal&size=1206x720)

**tailwindcss 從零開始學¹ - Day19 [完]**