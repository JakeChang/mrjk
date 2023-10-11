---
title: Vue3 從零開始學¹ - Day22 - Composition 函式
date: 2023-09-22 09:34:32
tags:
---
這個單元要來繼續介紹在 Composition API 的函式使用方法。

函式的宣告直接宣告在 `setup() {}` 即可，如果是要修改 ref 的變數時：

```html
<script>
import { ref, reactive } from 'vue';

export default {
  name: 'App',
  setup() {
    const count = ref(0);
    
    function incrementCount() {
      count.value++;
    }
    
    return {
      count,
      incrementCount,
    };
  },
};
</script>
```

在這裡宣告了一個函式 incrementCount()，會將變數 count 累加 1 ，所以修改其值不要忘記使用 .value，另外 return 時，也一併要將 incrementCount 這個函式 return 出去，在 `<template>` 內的按鈕才可以呼叫得到。

所以加上按鈕：

```html
<template>
  <p>{{ count }}</p>
  <button @click="incrementCount">button</button>
</template>

<script>
import { ref, reactive } from 'vue';

export default {
  name: 'App',
  setup() {
    const count = ref(0);
    
    function incrementCount() {
      count.value++;
    }
    
    return {
      count,
      incrementCount,
    };
  },
};
</script>
```

如果要讓函式可以修改用 reactive 宣告的變數：

```html
<template>
  <p>{{ state.count }}</p>
  <button @click="incrementCount">button</button>
</template>

<script>
import { ref, reactive } from 'vue';

export default {
  name: 'App',
  setup() {
    const state = reactive({
      count: 0,
    });
    
    function incrementCount() {
      state.count++;
    }

    return {
      state,
      incrementCount,
    };
  },
};
</script>
```

宣告了一個結構變數 state 裡面有一個變數 count，所以 incrementCount() 函式在修改結構變數 state.count 就不需要使用 .value，在 return 一樣，也要 return incrementCount 函式出去。

[今日程式碼範例](https://stackblitz.com/edit/vue-jo7hct?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day22 [完]**
