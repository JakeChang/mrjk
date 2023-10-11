---
title: Vue3 從零開始學¹ - Day14 - 元件傳入參數
date: 2023-09-14 19:21:31
tags:
---
在上一個單元已經學習到如何引用元件，這個單元就要針對元件來進行一些操作。

### 元件傳入參數

元件可以把資料傳給元件，那麼元件就必須要接收資料，修改 Header.vue：

```html
<template>
  <h1>Hello Component</h1>
  <p>{{ name }}</p>
</template>

<script>
export default {
  name: 'Header',
  props: ['name'],
};
</script>
```

probs 表示可以接收外部資料，這裡也宣告了一個變數 name 來進行接收。

所以呼叫元件時就可以傳入資料，修改 App.vue：

```html
<template>
  <Header name="Jake" />
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

這裡也必須要確實使用變數元件所宣告的 name 來把資料傳入。

### 元件傳入參數使用變數

第二個是這個傳入資料的方法，也不一定只能傳資料，也可以傳入變數資料：

```html
<template>
  <Header :name="name" />
</template>

<script>
import Header from './components/Header.vue';

export default {
  name: 'App',
  components: {
    Header,
  },
  data() {
    return {
      name: 'Allan',
    };
  },
};
</script>
```

宣告變數 name，然後將 `<Header name="Jake" />` 修改成 `<Header :name="name" />` 就表示在這裡的變數 name 傳入 Header 元件。

### 元件傳入參數定義型別

而在元件內，也可以指定傳入參數的型別，例如

```html
<template>
  <h1>Hello Component2</h1>
  <p>{{ name }}</p>
</template>

<script>
export default {
  name: 'Header2',
  props: {
    //定義型別
    name: String,
  },
};
</script>
```

### 元件傳入參數缺少時

另外一種情況是會希望元件內的接收變數可以有初始值：

```html
<template>
  <h1>Hello Component2</h1>
  <p>{{ email }}</p>
</template>

<script>
export default {
  name: 'Header2',
  props: {
    //定義型別
    email: {
      type: String,
      default: 'demo@demo',
    },
  },
};
</script>
```

所以如果引用元件，不帶入參數時：

```html
<template>
  <Header2 />
</template>

<script>
import Header2 from './components/Header2.vue';

export default {
  name: 'App',
  components: {
    Header2,
  },
};
</script>
```

則頁面就會顯示 email 的初始值，也就是 demo@demo

[今日程式碼範例](https://stackblitz.com/edit/vue-6sajez?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day14 [完]**