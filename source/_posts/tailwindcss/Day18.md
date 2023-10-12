---
title: tailwindcss 從零開始學¹ - Day18 - 表單 checkbox
date: 2023-09-25 06:20:47
tags:
---
這個單元繼續討論表單的元件，checkbox。

首先先宣告一個基本的 checkbox：

```html
<input type="checkbox" />
```

加入大小宣告，`h-5` 高度 5， `w-5` 寬度 5：

```html
<input type="checkbox" class="h-5 w-5" />
```

加入間隔宣告，`mt-1` 上方間隔 1， `mr-2` 右邊間隔 2：

```html
<input type="checkbox" class="h-5 w-5 mt-1 mr-2" />
```

加入邊界大小與顏色的宣告，`border` 顯示邊界，顏色為 `border-slate-900`，`bg-white` 背景顏色為白色：

```html
<input type="checkbox" class="h-5 w-5 mt-1 mr-2 border border-slate-900 bg-white" />
```

但這裡加入之後，可以發現其實與原本的 checkbox 不太有差別，必須要加入一個關鍵的屬性 `appearance-none` ，這個屬性可以消除原本的樣貌，而讓設定的寬線顏色顯示出來：

```html
<input type="checkbox" class="h-5 w-5 mt-1 mr-2 border bg-white appearance-none" />
```

加入當選擇時的屬性，`checked:` 後面接上顏色宣告，如 `checked:border-0` 選擇時邊界為 0，`checked:bg-gradient-to-tl`、`checked:from-gray-100`、`checked:to-slate-800` 選擇時背景顏色為漸層顏色：

```html
<input type="checkbox" class="h-5 w-5 mt-1 mr-2 border border-slate-900 bg-white appearance-none checked:border-0 checked:bg-gradient-to-tl checked:from-gray-100 checked:to-slate-800 relative float-left cursor-pointer align-top text-base" />
```

最後補上 `form` 表單與 `label` 元件宣告，並且加入 `relative`、`float-left` 顯示相對位置在左邊，`cursor-pointer` 滑鼠游標設定：

```html 
<form action="" class="mx-auto max-w-md">
  <label class="mb-2 font-bold text-gray-700">Email</label>

  <input type="checkbox" class="h-5 w-5 mt-1 mr-2 border border-slate-900 bg-white appearance-none checked:border-0 checked:bg-gradient-to-tl checked:from-gray-100 checked:to-slate-800 relative float-left cursor-pointer" />
</form>
```

[今日完整範例](https://play.tailwindcss.com/YWnabINbWz?layout=horizontal&size=1244x720)

**tailwindcss 從零開始學¹ - Day18 [完]**