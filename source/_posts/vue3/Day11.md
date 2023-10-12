---
title: Vue3 從零開始學¹ - Day11 - computed
date: 2023-09-11 09:28:44
tags:
---

從前幾個單元，對於函式的呼叫已經有一定程度的了解，這個單元來探討另外一種宣告函式的方式，`computed`。

先宣告一個簡單的函式：

```html
<script>
export default {
  name: 'App',
  methods: {
    testMethod() {
      console.log('testMethod');
    },
  },
};
</script>
```

而宣告 `computed` 的方式為：

```html
<script>
export default {
  name: 'App',
  methods: {
    testMethod() {
      console.log('testMethod');
    },
  },
  computed: {
    testComputed() {
      console.log('testComputed');
    },
  },
};
</script>
```

那麼，`computed` 與 `methods` 的差別是什麼？

`methods` 與 `computed` 的差別，`computed` 不管呼叫多少次，都只會執行一次，而 `methods` 呼叫幾次就會執行幾次，看以下的例子：

```html
<template>
  {{ testMethod() }}
  {{ testMethod() }}
  {{ testComputed }}
  {{ testComputed }}
</template>

<script>
export default {
  name: 'App',
  methods: {
    testMethod() {
      console.log('testMethod');
    },
  },
  computed: {
    testComputed() {
      console.log('testComputed');
    },
  },
};
</script>
```

分別呼叫 testMethod 與 testComputed 各兩次，會發現 testMethod 印出兩次，而 testComputed 只會印出一次。

至於這個 `console.log` 要去哪裡看？可以在 Chrome 瀏覽器按下檢視 -> 開發人員選項 -> JavaScript 控制台：

![https://ithelp.ithome.com.tw/upload/images/20230911/20162607QJ1ypXDnHC.png](https://ithelp.ithome.com.tw/upload/images/20230911/20162607QJ1ypXDnHC.png)

就會出現這個給開發人員專用的 debug 視窗：

![https://ithelp.ithome.com.tw/upload/images/20230911/20162607u8UbJ1hp2M.png](https://ithelp.ithome.com.tw/upload/images/20230911/20162607u8UbJ1hp2M.png)

使用 `console.log('')` 這個語法都會在這裡列印出來，是常用的一個開發手法。

那問題又來了，什麼時候會需要用到 `computed` ？

`computed` 可以用在一開始網頁執行時需要的判斷，看以下這個例子：

```html
<template>
  <div v-for="data in checkDatas" :key="data.id">
    {{ data.id }} {{ data.name }}
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      datas: [
        { id: 1, name: 'Jake' },
        { id: 2, name: 'Allan' },
        { id: 1, name: 'Eason' },
      ],
    };
  },
  computed: {
    checkDatas() {
      return this.datas.filter((data) => data.id === 1);
    },
  },
};
</script>
```

在這個例子宣告了一個 datas 陣列，裡面放了三組 key-value 的資料

在 `computed` 內宣告一個函式 checkDatas，而這個函式會將 id 等於 1 的資料篩選出來，這邊使用了一個快速篩選的方式 `filter`，`this.datas.filter((data) => data.id === 1)` 這個寫法就表示將陣列 datas 的資料一個一個走訪，然後找到 id 等於 1 的回傳成一個陣列出來。

最後在 template 內使用走訪陣列的方式來呼叫這個函式 checkDatas，所以網頁上就只會呈現這兩個資料：

```
1 Jake
1 Eason
```

所以簡單講，如果只需要單一次的複雜運算，官方會是建議使用 `computed` 來執行的。

[今日程式碼範例](https://stackblitz.com/edit/vue-uy9yy9?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day11 [完]**