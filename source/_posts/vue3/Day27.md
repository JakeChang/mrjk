---
title: Vue3 從零開始學¹ - Day27 - Composition 模組
date: 2023-09-27 09:24:24
tags:
---
這個單元繼續討論 Composition API，在模組的使用與 Option API 有什麼不同？這裡可以跟之前 [Day20 - 模組共用](https://ithelp.ithome.com.tw/articles/10316504) 來做一個比對。

首先，新增一個 Counter.js 檔案：

```javascript
import { ref } from 'vue';

export default function Counter() {
  const count = ref(0);
  
  function increment() {
    count.value++;
  }

  return {
    count,
    increment,
  };
}
```

這個給外部使用的函式 Counter，裡面宣告了一個變數 count 跟一個函式 increment，increment 會將變數 count 進行 +1 的動作，最後使用 `return` 回傳出去，代表外部也可以呼叫得到。

所以回到 App.vue ，就可以這樣引用 Counter.js：

```html
<template>
  {{ count }}
  <button @click="increment">button</button>
</template>

<script>
import Counter from './Counter';

export default {
  name: 'App',
  setup() {
    const { count, increment } = Counter();

    return {
      count,
      increment,
    };
  },
};
</script>
```

在 `setup` 內直接引用 const { count, increment } = Counter(); ，就可以使用變數 count 跟 increment 函式了。

但有的時候，會需要這個 Counter() 可以從外部設定初始值跟累加的數值，所以會需要多兩個變數給外部傳入，修改 Counter.js：

```html
import { ref } from 'vue';

// startIndex, step 給外部輸入的參數
export default function Counter(startIndex, step) {
  const count = ref(startIndex);

  function increment() {
    count.value += step;
  }

  return {
    count,
    increment,
  };
}
```

Counter 多了兩個傳入的變數值 startIndex 與 step。

回到 App.vue 就可以這樣呼叫 Counter：

```html
<template>
  {{ count }}
  <button @click="increment">button</button>
</template>

<script>
import Counter from './Counter';

export default {
  name: 'App',
  setup() {
    const { count, increment } = Counter(1000, 100);

    return {
      count,
      increment,
    };
  },
};
</script>
```

直接在 Counter(1000, 100); 帶入想要的初始值與累加的數值即可。

[今日程式碼範例](https://stackblitz.com/edit/vue-vnkhs3?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day27 [完]**