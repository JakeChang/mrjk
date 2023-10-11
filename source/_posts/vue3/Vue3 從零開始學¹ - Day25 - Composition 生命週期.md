---
title: Vue3 從零開始學¹ - Day25 - Composition 生命週期
date: 2023-09-25 05:55:10
tags:
---
這個單元繼續討論 Composition API，那麼在生命週期上與 Option API 的寫法上有什麼不同？

與之前 [Day19](https://ithelp.ithome.com.tw/articles/10316501) 介紹的 Option API 有所不同，只剩下 `onBeforeMount`, `onMounted`, `onBeforeUpdate`, `onUpdated`, `onBeforeUnmount`, `onUnmounted` 這些生命週期可以呼叫，例如：

```html
<template>
</template>

<script>
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
  ref,
} from 'vue';

export default {
  name: 'App',
  setup() {
    onBeforeMount(() => {
      console.log('onBeforeMount');
    });
    onMounted(() => {
      console.log('onMounted');
    });
    onBeforeUpdate(() => {
      console.log('onBeforeUpdate');
    });
    onUpdated(() => {
      console.log('onUpdated');
    });
    onBeforeUnmount(() => {
      console.log('onBeforeUnmount');
    });
    onUnmounted(() => {
      console.log('onUnmounted');
    });
  },
};
</script>
```

此外，也可以將與 UI 邏輯相關的程式放在 `onMounted` 裡：

```html
<template>
  <input type="text" ref="inputRef" />
</template>

<script>
import { onMounted, ref } from 'vue';

export default {
  name: 'App',
  setup() {
    const inputRef = ref(null);

    onMounted(() => {
      console.log('onMounted');

      //測試 onMounted
      inputRef.value.focus();
    });
    
    return {
      inputRef,
    };
  },
};
</script>
```

在這裡放使用了 `inputRef.value.focus();` 一樣是網頁呈現完成後，可以直接指定 `<input type="text" ref="inputRef" />` 這個輸入框。

[今日程式碼範例](https://stackblitz.com/edit/vue-apuqa9?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day25 [完]**

