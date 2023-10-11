---
title: Vue3 從零開始學¹ - Day10 - 表單 submit
date: 2023-09-10 12:46:47
tags:
---
在一個正常的表單流程之中，填完所有欄位之後，會有一個送出按鈕，按下這個送出按鈕之後，資料才會送出去。但如果將所有表單欄位宣告出來的，會需要宣告一堆變數，在程式碼上很難維護，所以在這邊宣告一個結構變數來儲存所有的表單欄位變數：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      formData: {
        name: '',
      },
    };
  },
};
</script>
```

用一個結構變數 formData 來宣告所有的表單變數，所以在 formData 裡面又宣告了一個 name 變數。這個結構變數的用法就會變成：

```html
<template>
  {{ formData.name }}
</template>
```

接下來把所有的表單欄位變數宣告完成：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      formData: {
        name: '',
        text: '',
        selectValue: '',
        isCheck: false,
        checkbox: [],
        radio: '',
      },
    };
  },
};
</script>
```

跟上一個單元一樣，宣告所有的表單欄位，但差別在於使用 v-model 進行綁定時，要修改成結構變數：

```html
<template>
  <input type="text" v-model="formData.name" />
  <br />

  <textarea v-model="formData.text" />
  <br />

  <select v-model="formData.selectValue">
    <option value="">select</option>
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
  </select>
  <br />

  <input type="checkbox" v-model="formData.isCheck" /> is check
  <br />

  <input type="checkbox" value="0" v-model="formData.checkbox" /> 0
  <input type="checkbox" value="1" v-model="formData.checkbox" /> 1
  <input type="checkbox" value="2" v-model="formData.checkbox" /> 2
  <input type="checkbox" value="3" v-model="formData.checkbox" /> 3
  <br />

  <input type="radio" value="0" v-model="formData.radio" /> 0
  <input type="radio" value="1" v-model="formData.radio" /> 1
  <input type="radio" value="2" v-model="formData.radio" /> 2
  <input type="radio" value="3" v-model="formData.radio" /> 3
  <br />
</template>
```

剩下最後一個步驟，宣告表單的按鈕：

```html
<button @click="submit">送出</button>
```

在這裡會用 `@click` 來將按鈕按下去的觸發事件與函式 `submit` 結合，這裡在之前 [Day7](https://ithelp.ithome.com.tw/articles/10315665) 按鈕按下去會累加 1 的範例一模一樣，忘記的朋友可以回去複習一下。

宣告這個 submit 函式：

```javascript
methods: {
  submit() {
    console.log(this.formData);
  },
},
```

在這裡只要先將這個結構變數印出來就好，因為按照表單送出流程，會需要去呼叫 Server API 來做後續處理，在這個單元，先不講解如何呼叫 API，之後的單元再來慢慢討論。

完整程式碼：

```html
<template>
  <input type="text" v-model="formData.name" />
  <br />

  <textarea v-model="formData.text" />
  <br />

  <select v-model="formData.selectValue">
    <option value="">select</option>
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
  </select>
  <br />

  <input type="checkbox" v-model="formData.isCheck" /> is check
  <br />

  <input type="checkbox" value="0" v-model="formData.checkbox" /> 0
  <input type="checkbox" value="1" v-model="formData.checkbox" /> 1
  <input type="checkbox" value="2" v-model="formData.checkbox" /> 2
  <input type="checkbox" value="3" v-model="formData.checkbox" /> 3
  <br />

  <input type="radio" value="0" v-model="formData.radio" /> 0
  <input type="radio" value="1" v-model="formData.radio" /> 1
  <input type="radio" value="2" v-model="formData.radio" /> 2
  <input type="radio" value="3" v-model="formData.radio" /> 3

  <button @click="submit">送出</button>
  <hr />

  {{ formData }}
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      formData: {
        name: '',
        text: '',
        selectValue: '',
        isCheck: false,
        checkbox: [],
        radio: '',
      },
    };
  },
  methods: {
    submit() {
      console.log(this.formData);
    },
  },
};
</script>
```

[今日程式碼範例](https://stackblitz.com/edit/vue-gwrwuy?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day10 - form [完]**