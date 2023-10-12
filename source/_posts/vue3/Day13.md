---
title: Vue3 從零開始學¹ - Day13 - 元件
date: 2023-09-13 12:34:41
tags:
---
從這個單元開始要進入模組化的世界，當程式碼越寫越多時，為了方便維護，會將共用的程式碼寫成一個一個的模組，稱為模組化。

在 Vue3 的定義中，這個模組稱為 `component`，中文翻譯為元件或組件，所以本文還是用元件來稱呼。

先來看看一個基本的元件，新增一個檔案 Header.vue，然後先寫上基本架構：

```html
<template>
  <h1>Hello Component</h1>
</template>

<script>
export default {
  name: 'Header',
};
</script>
```

Header.vue 這個檔案就是要用來元件化的檔案，所以在 Vue3 之中，將程式碼元件化的過程，就只是把共用的程式碼檔案分離出來而已。

所以現在會有兩個 .vue 檔案，App.vue 與 Header.vue，要如何讓 App.vue 可以引用 Header.vue 這個檔案呢？

在這裡先將 App.vue 修改回最基本的架構：

```html
<template>
</template>

<script>
export default {
  name: 'App',
};
</script>
```

要引用其它檔案，必須要使用 `import`，所以將 App.vue 修改成：

```html
<template>
</template>

<script>
import Header from 'Header.vue';

export default {
  name: 'App',
};
</script>
```

但這樣還不夠，`import` 完成，需要宣告這個模組，宣告的方式是使用 `components: {}`：

```html
<template>
</template>

<script>
import Header from 'Header.vue';

export default {
  name: 'App',
  components: {
    Header,
  },
};
</script>
```

`import` 進來的元件檔案為 Header，然後在 `components` 內宣告這個 Header，這樣就可以在 `<template></template>` 中使用這個模組了：

```html
<template>
  <Header />
</template>

<script>
import Header from 'Header.vue';

export default {
  name: 'App',
  components: {
    Header,
  },
};
</script>
```

最後，為了管理方便，通常都會將所有元件放到資料夾內，所以可以新增一個資料夾，將 Header.vue 移入，所以 `import` 的地方就必須修改成：

```html
<template>
  <Header />
</template>

<script>
import Header from './components/Header.vue';

export default {
  name: 'App',
  components: {
    Header,
  },
};
</script>
```

[今日程式碼範例](https://stackblitz.com/edit/vue-zvqx7q?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day13 - [完]**