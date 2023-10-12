---
title: Vue3 從零開始學¹ - Day15 - 元件數值傳出
date: 2023-09-15 15:01:03
tags:
---
在上一個單元，學習到了如何從上層傳資料給子元件，也就是由上而下，但有得時候會需要有下而上，也就是從子元件傳資料給上層。

這個單元會將表單的輸入框，切成元件後，傳出輸入框所輸入的資料給上層。

首先先宣告好表單的輸入框，這裡的宣告在之前 [Day8](https://ithelp.ithome.com.tw/articles/10315825) 有詳細的介紹：

```html
<template>
  <div>
    <input type="text" v-model="text" />
    <button>Send</button>
  </div>
</template>

<script>
export default {
  name: 'View',
  data() {
    return {
      text: '',
    };
  },
};
</script>
```

將以上的程式碼儲存成在 components/View.vue。

然後在 App.vue 引用這個元件：

```html
<template>
  <View />
</template>

<script>
import View from './components/View.vue';

export default {
  name: 'App',
  components: {
    View,
  },
};
</script>
```

接下來回到 components/View.vue，要從元件內傳資料給上層，要先宣告 emits：

```javascript
emits: ['viewText']
```

宣告一個 emits ，給予一個陣列，裡面有一個變數 viewText。

然後在表單的按鈕呼叫這個 emits 內的變數，並且把資料傳入：

```html
<button @click="$emit('viewText', text)">Send</button>
```

組合起來：

```html
<template>
  <div>
    <input type="text" v-model="text" />
    <button @click="$emit('viewText', text)">Send</button>
  </div>
</template>

<script>
export default {
  name: 'View',
  emits: ['viewText'],
  data() {
    return {
      text: '',
    };
  },
};
</script>
```

接下來再度回到 App.vue，宣告一個變數 text 來接收元件傳出來的資料：

```html
<template>
  <View />
  <br />
  {{ text }}
</template>

<script>
import View from './components/View.vue';

export default {
  name: 'App',
  components: {
    View,
  },
  data() {
    return {
      text: '',
    };
  },
};
</script>
```

最後使用一個函式 getViewText，來接收資料：

```html
<template>
  <View @viewText="getViewText" />
  <br />
  {{ text }}
</template>

<script>
import View from './components/View.vue';

export default {
  name: 'App',
  components: {
    View,
  },
  data() {
    return {
      text: '',
    };
  },
  methods: {
    getViewText(text) {
      this.text = text;
    },
  },
};
</script>
```

如此一來，當按下按鈕時，元件內的表單變數 text，就可以傳出去給 App.vue 來接收了。

[今日程式碼範例](https://stackblitz.com/edit/vue-dwu4w5?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day15 [完]**