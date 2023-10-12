---
title: Vue3 從零開始學¹ - Day4 - if 判斷式
date: 2023-09-04 12:19:00
tags:
---

在上一個單元，已經學習到如何顯示 Hello World，這個最基礎的知識之後。接下來繼續打基礎，從這個單元開始，會接觸各種程式邏輯判斷的方法，會先從 if 判斷開始，首先先來看看什麼是 if 判斷。

一樣跟上一個單元一樣，宣告一個變數 `isShow`，但這裡的變數的型別是使用布林型別，只有 `true` 與 `false` 兩種值，將其設定為 `true`：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      isShow: true,
    };
  },
};
</script>
```

接下來使用 if 判斷式來判斷這個變數 `isShow` 是不是等於 `true`，如果等於 `true` 的話才會顯示內容，否則的話就不顯示。在 Vue3 使用 if 判斷式是使用 `v-if` 這個關鍵字：

```html
<p v-if="isShow">Hello World</p>
```

所以將程式碼結合起來：

```html
<template>
  <p v-if="isShow">Hello World</p>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      isShow: true,
    };
  },
};
</script>
```

在 `data(){}` 內宣告了一個布林變數為 `isShow`，在 template 之中使用 Vue3 標籤 `v-if` 並且指定變數為 `isShow`，就可以使用 `isShow` 這個變數來控制是否顯示 Hello World 這樣的內容。

可以把 `isShow` 修改為 `false`，然後看看 Hello World 是不是還會顯示。

if 判斷式也可以加入 else 的判斷語法，`v-if` 跟 `v-else-if`。先宣告一個變數 x 等於 2：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      x: 2,
    };
  },
};
</script>
```

然後加入 v-if 與 v-else-if 判斷：

```html
<template>
  <p v-if="x === 0">x = 0</p>
  <p v-else-if="x === 1">x = 1</p>
  <p v-else-if="x === 2">x = 2</p>
  <p v-else>x != 0</p>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      x: 2,
    };
  },
};
</script>
```

這個多重的 if else 結構是指，如果 x 等於 0 的話就顯示 x = 0，否則 x 等於 1 的話就顯示 x = 1，否則 x 等於 2 的話就顯示 x = 2，如果都不等於 0 且也不等於 1 且也不等於 2 的話就顯示 x != 0 。

最後， `v-show` 跟 `v-if` 會有一樣的效果，將 `v-if` 改成 `v-show`：

```html
<template>
  <p v-show="isShow">Hello World</p>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      isShow: true,
    };
  },
};
</script>
```

`v-show` 與 `v-if` 的差別在於，無法像 `v-if` 一樣可以寫多重的 if 判斷，另外如果 `v-show` 不顯示的話，會在 html 上顯示：

```html
 <p style="display: none;">Hello World</p>
```

而 `v-if` 不顯示的話，會變成連 html 標籤都會消失不見。

[今日程式碼範例](https://stackblitz.com/edit/vue-vwwjgv?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day4 [完]**