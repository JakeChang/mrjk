---
title: tailwindcss 從零開始學¹ - Day28 - 使用插件
date: 2023-10-05 12:43:29
tags:
---
雖然在 tailwindcss 可以製作出豐富的 UI 元件，但還是有許多已經寫好的元件可以直接使用，不需要重複製作輪子。

這個單元將討論 tailwindcss 插件的安裝與使用方式，這裡介紹一個文章閱讀的版面插件。

要製作這個文章閱讀版面需要安裝外掛套件，先安裝套件 typography：

```shell
npm install -D @tailwindcss/typography
```

在 tailwind.config.js 檔案新增 plugin：

```js
module.exports = {
  theme: {
    // ...
  },
  plugins: [
    require('@tailwindcss/typography'),
    // ...
  ],
}
```

接下來就可以直接在 html 套用這個插件的樣式，一個最簡單的文章閱讀版型：

```html
<article class="prose lg:prose-xl">
  <h1>Garlic bread with cheese: What the science tells us</h1>
  <p>
    For years parents have espoused the health benefits of eating garlic bread with cheese to their
    children, with the food earning such an iconic status in our culture that kids will often dress
    up as warm, cheesy loaf for Halloween.
  </p>
  <p>
    But a recent study shows that the celebrated appetizer may be linked to a series of rabies cases
    springing up around the country.
  </p>
  <!-- ... -->
</article>
```

就會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20231005/201626070KVF2CBYV1.png](https://ithelp.ithome.com.tw/upload/images/20231005/201626070KVF2CBYV1.png)

接下來根據這個模板，改良成為最好看的版型：

```html
<div class="mx-auto max-w-4xl px-4 py-16 text-xl tracking-wide sm:py-24 sm:px-6 md:px-12">
  <article class="prose lg:prose-xl">
    <h1>Garlic bread with cheese: What the science tells us</h1>
    <p>For years parents have espoused the health benefits of eating garlic bread with cheese to their children, with the food earning such an iconic status in our culture that kids will often dress up as warm, cheesy loaf for Halloween.</p>
    <p>But a recent study shows that the celebrated appetizer may be linked to a series of rabies cases springing up around the country.</p>
    <!-- ... -->
  </article>
</div>
```

就會呈現這個樣子：

![https://ithelp.ithome.com.tw/upload/images/20231005/20162607NlfvAW8h0h.png](https://ithelp.ithome.com.tw/upload/images/20231005/20162607NlfvAW8h0h.png)

[今日完整範例](https://play.tailwindcss.com/bOAqEat6rV?layout=horizontal)

**tailwindcss 從零開始學¹ - Day28 [完]**