---
title: Vue3 從零開始學¹ - Day16 - 元件更新
date: 2023-09-16 09:17:08
tags:
---

在上一個單元是將元件傳出資料給上層，但還是必須要透過一個按鈕才可以觸發事件，能不能有自動偵測的方式做到？

這個單元就要來繼續討論元件，元件可以自動把資料傳出給上層。

首先宣告一個元件檔案 components/Input.vue：

```html
<template>
  <input type="text" />
</template>

<script>
export default {
  name: 'Input',
};
</script>
```

要將資料自動傳出，必須要宣告 props：

```html
<template>
  <input type="text" />
</template>

<script>
export default {
  name: 'Input',
  props: {
    modelValue: String, // modelValue 為系統名稱，不能自由命名
  },
};
</script>
```

這裡要注意的是 modelValue 為系統名稱，不能自由命名。

接著在 `input` 內宣告 `:value` 指定這個 `modelValue`，等於是先將 `input` 內輸入的資料暫存起來。然後再透過
`@input="$emit('update:modelValue', $event.target.value)"` 這一段長長的指令將內容更新給上層。

```html
<template>
  <input
    type="text"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<script>
export default {
  name: 'Input',
  props: {
    modelValue: String,
  },
};
</script>
```

`$emit` 可以在元件內發出事件，而這裡帶入的事件就是 `update:modelValue` ，也就是表示當 `modelValue` 被更新時，會觸發這個事件，最後再使用 `@input` 來偵測是否有輸入內容。

回到 App.vue，宣告一個變數 name，然後直接使用 `v-model` 來綁定元件與變數 name 即可。

```html
<template>
  {{ name }}
  <Input v-model="name" />
</template>

<script>
import Input from './components/Input.vue';

export default {
  name: 'App',
  components: {
    Input,
  },
  data() {
    return {
      name: '',
    };
  },
};
</script>
```

[今日程式碼範例](https://stackblitz.com/edit/vue-sthvet?file=src%2Fcomponents%2FInput.vue)

**Vue3 從零開始學¹ - Day16 [完]**