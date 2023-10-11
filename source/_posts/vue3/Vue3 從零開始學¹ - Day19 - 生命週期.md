---
title: Vue3 從零開始學¹ - Day19 - 生命週期
date: 2023-09-19 09:39:33
tags:
---
生命週期指的就是一個 .vue 檔案，被瀏覽器載入完成所產生的一連串的執行順序。

除了先前幾個單元介紹的 `data(){}` 是宣告變數的地方，`methods: {}` 是宣告函式的地方，還有許多的其它的初始化的方法，如 `beforeCreate` 、 `created` 、 `beforeMount` 、 `mounted`，看一下以下的範例：

```html
<template>
  <button @click="show">Load Component</button>
  <Component v-if="isShow" />
  <br />
</template>

<script>
import Component from './components/Component.vue';

export default {
  name: 'App',
  components: {
    Component,
  },
  beforeCreate() {
    console.log('beforeCreate');
  },
  created() {
    console.log('created');
  },
  beforeMount() {
    console.log('beforeMount');
  },
  mounted() {
    console.log('mounted');
  },
  data() {
    return {
      isShow: false,
    };
  },
  methods: {
    show() {
      this.isShow = !this.isShow;
    },
  },
};
</script>
```

如果有這樣的宣告，其呼叫的順序會是：beforeCreate → created → beforeMount → mounted，也就是會先執行 beforeCreate 裡面的程式，然後才執行 created 裡面的程式，依序以此類推。

因為這裡有引用 Component.vue 這個元件，如果這個元件內也有一樣的宣告，如：

```html
<template>
  <p>Component</p>
</template>

<script>
export default {
  name: 'Component',
  beforeCreate() {
    console.log('Component beforeCreate');
  },
  created() {
    console.log('Component created');
  },
  beforeMount() {
    console.log('Component beforeMount');
  },
  mounted() {
    console.log('Component mounted');
  },
};
</script>
```

那呼叫的順序會變成是， beforeCreate → created → beforeMount → Component beforeCreate → Component created → Component beforeMount → Component created → mounted。

另外如果有元件引用，還可以再加入兩個生命週期，beforeUpdate 與 updated，修改一下 App.vue：

```html
<template>
  <button @click="show">Load Component</button>
  <Component v-if="isShow" />
  <br />
</template>

<script>
import Component from './components/Component.vue';

export default {
  name: 'App',
  components: {
    Component,
  },
  beforeCreate() {
    console.log('beforeCreate');
  },
  created() {
    console.log('created');
  },
  beforeMount() {
    console.log('beforeMount');
  },
  mounted() {
    console.log('mounted');
  },
  beforeUpdate() {
    console.log('beforeUpdate');
  },
  updated() {
    console.log('updated');
  },
  data() {
    return {
      isShow: false,
    };
  },
  methods: {
    show() {
      this.isShow = !this.isShow;
    },
  },
};
</script>
```

修改一下 components/Component.vue：

```html
<template>
  <p>Component</p>
</template>

<script>
export default {
  name: 'Component',
  beforeCreate() {
    console.log('Component beforeCreate');
  },
  created() {
    console.log('Component created');
  },
  beforeMount() {
    console.log('Component beforeMount');
  },
  mounted() {
    console.log('Component mounted');
  },
  beforeUpdate() {
    console.log('Component beforeUpdate');
  },
  updated() {
    console.log('Component updated');
  },
};
</script>
```

因為 isShow: false，所以還不會呼叫元件的呼叫順序為：beforeCreate → created → beforeMount → mounted。

按下按鈕之後的順序會變成：beforeUpdate → Component beforeCreate → Component created → Component beforeMount → Component created → updated。

使用生命週期的好處是什麼？

就是可以分門別類要處理的邏輯，例如如果有呼叫 Server API 的話，通常會放在 `created() {}` 來呼叫。或者有 UI 的相關邏輯處理，會放在 `mounted() {}` 。

例如這個頁面會在一開始就直接將 foucs 放在 input 內：

```html
<template>
  <!-- mounted -->
  <input type="text" ref="inputRef" />
</template>

<script>
export default {
  name: 'App',
  mounted() {
    console.log('mounted');

    //UI控制
    this.$refs.inputRef.focus();
  },
};
</script>
```

[今日程式碼範例](https://stackblitz.com/edit/vue-lqoetn?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day19 [完]**
