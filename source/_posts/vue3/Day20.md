---
title: Vue3 從零開始學¹ - Day20 - 模組共用
date: 2023-09-20 08:59:05
tags:
---
這個單元要來介紹另外一種模組化的方式，先前都是介紹整個 .vue 的元件可以獨立分開，有的時候會需要函式的模組化。

一開始，先宣告一個按鈕，這個按鈕一樣按下去會累加 1：

```html
<template>
  {{ count }}
  <button @click="incrementCount">Add Count</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: 100,
    };
  },
  methods: {
    incrementCount() {
      this.count += 1;
    },
  },
};
</script>
```

上述的方法是常見的做法，這個時候如果在別的 .vue 檔案也需要這個累加 1 的函式，該如何是好呢？總不可能重複在另外一個 .vue 再度寫上這些程式邏輯嗎？那也只會造成日後維護的困難度增加而已。

在這裡可以把累加的這個函式先獨立出來另外一個程式檔案，新建一個程式 Count.js：

```html
export default {
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    incrementCount() {
      this.count += 1;
    },
  },
};
```

可以看出這個 Count.js 裡面有一個 incrementCount() 會把變數 count 進行累加。

而在 App.vue 就可以使用引用的方式來呼叫這個函式，修改 App.vue：

```html
<template>
  {{ count }}
  <button @click="incrementCount">Add Count</button>
</template>

<script>
import Count from './Count';

export default {
  name: 'App',

  //加入模組
  mixins: [Count],
};
</script>
```

使用 mixins 的方式，將所引用的 Count 加入到這裡可以來使用。所以按下按鈕之後，依然可以累加 1，並且呈現出來。

[今日程式碼範例](https://stackblitz.com/edit/vue-utgjmp?file=src%2Fmain.js)

**Vue3 從零開始學¹ - Day20 [完]**