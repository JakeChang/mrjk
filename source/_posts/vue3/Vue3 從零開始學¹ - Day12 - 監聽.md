---
title: Vue3 從零開始學¹ - Day12 - 監聽
date: 2023-09-12 12:21:05
tags:
---
接下來這個單元來討論監聽，什麼是監聽呢？

首先，根據之前所學到的，新增一個按鈕，這個按鈕按下去會呼叫一個函式：

```html
<template>
  {{ count }}
  <br />
  <button @click="addCount">Add Count</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    addCount() {
      this.count += 1;
    },
  },
};
</script>
```

這個 `button` 加入一個 `click` 事件，會呼叫函式 addCount，而這個 addCount 會將變數 count 累加 1，相信有完整看過之前的單元，對這些語法內容一定不陌生。

那麼要如何建立監聽事件？

監聽必須要使用 `watch`：

```javascript
watch: {
},
```

由於這邊要監聽的是變數 count，所以將 `watch` 修改成：

```javascript
watch: {
  count(newValue, oldValue) {
    console.log(newValue, oldValue);
  },
},
```

count 會傳入兩個變數，newValue 與 oldValue 這兩個值。顧名思義，就是傳入 count 的上一個值與新的值，所以如果按下按鈕一次，會列印出：

```html
1 0
```

如果按下按鈕 3 次，會列印出：

```html
1 0
2 1
3 2
```

`watch` 可以監聽變數，記憶著最新的值與上一個值。

此外，`watch` 也可以監聽物件變數，宣告一個物件變數 user，裡面再宣告一個字串 name：

```html
<template>
  <input type="text" v-model="user.name" />
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      user: {
        name: '',
      },
    };
  },
};
</script>
```

這邊在 `watch` 內加入監聽的方式需使用 `handler`，並且設定 `deep` 為 true，監聽物件時，才能有作用：

```html
<template>
  <input type="text" v-model="user.name" />
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      user: {
        name: '',
      },
    };
  },
  watch: {
    user: {
      handler(newValue) {
        console.log(newValue);
      },
      deep: true, //要監聽物件時，要設定才會起作用
    },
  },
};
</script>
```

這個輸入框輸入三次就會列印出：

```
{name: "1"}
{name: "11"}
{name: "111"}
```

最後，陣列也可以被 `watch`，宣告一個陣列 items，加入 `watch`：

```html
<template>
  <button @click="addItem">Add item</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      items: [],
    };
  },
  methods: {
    addItem() {
      this.items.push('test');
    },
  },
  watch: {
    items: {
      handler(newValue) {
        console.log(newValue);
      },
      deep: true, //要監聽陣列時，要設定才會起作用
    },
  },
};
</script>
```

一樣在 `watch` 內加入監聽的 `handler`，並且設定 `deep` 為 true，監聽物件時，才能有作用。

這個按鈕按下三次就會列印出：

```html
["test"]
["test", "test"]
["test", "test", "test"]
```

`watch` 可以用在當需要變數的某一個值被觸發時，例如當數值累加到 10 會跳出警告等。

[今日程式碼範例](https://stackblitz.com/edit/vue-v4fviv?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day12 [完]**