---
title: Vue3 從零開始學¹ - Day9 - 表單常用欄位
date: 2023-09-09 09:15:18
tags:
---

上一個單元學習到了表單中的 `input` 輸入框與 Vue3 的綁定，但在表單中，還有許多其它的輸入欄位，接下來這個單元繼續討論其它常用的表單欄位。

### 多行的輸入文字框 Textarea

這個欄位的使用方式跟 `input` 欄位一樣，使用單一變數的方式：

```html
<template>
  {{ text }} <br />
  <textarea v-model="text" />
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      text: '',
    };
  },
};
</script>
```

這裡宣告一個變數 text，型別字串，初始化為空白，一樣使用 `v-model` 綁定到 `textarea`。所以這裡會將 `textarea` 的內容，存入到 text 變數內。

### 下拉式選單 select

```html
<template>
  {{ selectValue }} <br />
  <select v-model="selectValue">
    <option value="">select</option>
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
  </select>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      selectValue: '',
    };
  },
};
</script>
```

這裡宣告一個變數 selectValue，型別字串，初始化為空白，一樣使用 `v-model` 綁定到 `select`。所以這裡會將 `select` 的 value 的值，存入到 selectValue 變數內。

### 單一選擇 checkbox

```html
<template>
  {{ isCheck }} <br />
  <input type="checkbox" v-model="isCheck" /> is check
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      isCheck: false,
    };
  },
};
</script>
```

這裡宣告一個變數 isCheck，型別布林，初始化為 false，一樣使用 `v-model` 綁定到 `checkbox`。所以如果 `checkbox` 是勾選的狀態，isCheck 會被存入 true。 `checkbox` 不是勾選的狀態，isCheck 就會被存入 false。

### 多選 checkbox

```html
<template>
  {{ checkbox }} <br />
  <input type="checkbox" value="0" v-model="checkbox" /> 0
  <input type="checkbox" value="1" v-model="checkbox" /> 1
  <input type="checkbox" value="2" v-model="checkbox" /> 2
  <input type="checkbox" value="3" v-model="checkbox" /> 3
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      checkbox: [],
    };
  },
};
</script>
```

這裡宣告一個變數 checkbox，型別陣列，初始化為空陣列，一樣使用 `v-model` 綁定到 `checkbox`。所以這裡會將勾選 checkbox 內的 value 值，存入到 checkbox 陣列內。

### 單選 radio 

```html
<template>
  {{ radio }} <br />
  <input type="radio" value="0" v-model="radio" /> 0
  <input type="radio" value="1" v-model="radio" /> 1
  <input type="radio" value="2" v-model="radio" /> 2
  <input type="radio" value="3" v-model="radio" /> 3
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      radio: '',
    };
  },
};
</script>
```

這裡宣告一個變數 radio，型別陣列，初始化為空白，一樣使用 `v-model` 綁定到 `radio`。所以這裡會將勾選 radio 內的 value 值，存入到 radio 變數內。

以上就是常見使用的表單欄位的方法。

[今日程式碼範例](https://stackblitz.com/edit/vue-1gpjcv?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day9 [完]**

