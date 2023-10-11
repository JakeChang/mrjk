---
title: Vue3 從零開始學¹ - Day8 - 表單 input
date: 2023-09-08 09:41:39
tags:
---

在上一個單元學習到了如何控制按鈕按下去所產生的事件，有了製作按鈕的經驗之後，在網頁上最常使用的輸入方式就是表單，也是在開發上最容易遇到的需求。

第一個最常使用的表單就是 `input` ，先宣告一個 `input`：

```html
<template>
  <input type="text" />
</template>
```

要讓這個表單與 Vue3 的邏輯產生連結，會需要宣告一個變數，且型別是字串：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      name: '',
    };
  },
};
</script>
```

這裡宣告了一個變數 name，初始值是空白。而要讓變數 name 與 `input` 產生連結，需要使用 `v-model` 來產生綁定，就是關聯這兩個部分：

```html
<template>
  <input type="text" v-model="name" />
</template>
```

使用 `v-model` 並且給予變數 name，就可以讓 name 與 `input` 綁定起來。

最後再把 name 顯示出來即可：

```html
<template>
  {{ name }} <br />
  <input type="text" v-model="name" />
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      name: '',
    };
  },
};
</script>
```

當直接開啟網頁時，在 `input` 輸入框，輸入文字時，神奇的事情發生了，name 會自動顯示其 `input` 內容的值，而這個就是 `v-model` 所綁定的效果。

而除了使用 `v-model` 來進行變數綁定之外，Vue3 也針對了 `v-model` 提供額外的邏輯判斷。

例如 `v-model.trim` 可以去除前後空白：

```html
<template>
  {{ name }} <br />
  <input type="text" v-model.trim="name" />
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      name: '',
    };
  },
};
</script>
```

`v-model.lazy` 可以在輸入完畢才會將內容儲存起來，換句話說就是將游標跳出，`input` 輸入框才會將值寫入到變數內：

```html
<template>
  {{ name }} <br />
  <input type="text" v-model.lazy="name" />
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      name: '',
    };
  },
};
</script>
```

`v-once` 可以防止顯示的變數被更改，但其實只是不顯示被更新的值而已：

```html
<template>
  <p v-once>{{ message }}</p>
  <br />
  <input type="text" v-model="message" />
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      message: 'Hello',
    };
  },
};
</script>
```

`v-pre` 可以完全顯示標籤的內容，也就是在 `<p></p>` 裡面是什麼內容就顯示什麼內容：

```html
<template>
  <p v-pre>{{ name }}</p>
  <br />
  <input type="text" v-model="name" />
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      name: '',
    };
  },
};
</script>
```

以上這個例子就會顯示：

```html
{{ name }}
```

當然表單還有許多的控制選項可以使用，例如下拉式選單、checkbox ...等，這些將會在下一個單元繼續討論。

[今日程式碼範例](https://stackblitz.com/edit/vue-9vtdaq?file=src%2FApp.vue)

### 關於鐵人賽

前端開發不會只有 Vue3.js 的工具要學習，還必須要學習如何網頁排版，這裡推薦從今日開始接收的另外一個挑戰：

[tailwindcss - 從零開始學](https://ithelp.ithome.com.tw/users/20162607/ironman/6658)

這兩個挑戰，最後幾個單元會相連起來，變成一個共同思路的學習方式。

**Vue3 從零開始學¹ - Day8 - [完]**