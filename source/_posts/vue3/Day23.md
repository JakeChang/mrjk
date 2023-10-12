---
title: Vue3 從零開始學¹ - Day23 - Composition input
date: 2023-09-23 08:26:55
tags:
---
這個單元要來繼續探討 Composition ，而在 Composition API 使用表單的 input 又有哪邊不一樣？

宣告 `ref` 變數與 input：

```html
<template>
  {{ name }}
  <input type="text" v-model="name" />
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'App',
  setup() {
    const name = ref('');
    
    return {
      name,
    };
  },
};
</script>
```

使用 `ref` ，跟 input 進行 `v-model` 綁定時，與使用 Option API 並沒有什麼太大不同。

換宣告 `reactive` 變數時：

```html
<template>
  {{ email }}
  <input type="text" v-model="email" />
</template>

<script>
import { reactive, toRefs } from 'vue';

export default {
  name: 'App',
  setup() {
    const user = reactive({
      email: '',
    });
    
    return {
      ...toRefs(user),
    };
  },
};
</script>
```

在這裡 `reactive` 變數要跟 input 進行 `v-model` 綁定之前，要先使用 ...toRefs 進行封裝起來，然後 return 出去。

[今日程式碼範例](https://stackblitz.com/edit/vue-segynp?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day23 [完]**