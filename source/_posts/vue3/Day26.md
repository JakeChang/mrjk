---
title: Vue3 從零開始學¹ - Day26 - Composition 元件
date: 2023-09-26 09:14:24
tags:
---
這個單元繼續討論 Composition API，在元件的使用與 Option API 有什麼不同？

首先，先宣告一個元件檔案 Component.vue，檔案放在 /components/Component.vue：

```html
<template>
  {{ thisName }}
  <br />
  <button @click="sendValue">傳出</button>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  name: 'Component',
  props: ['name'],
  setup(props, context) {
    const thisName = ref('');

    onMounted(() => {
      console.log("onMounted", props.name);
      thisName.value = props.name;
    });
    
    return {
      thisName,
    };
  },
};
</script>
```

在這個元件檔案中，宣告 `props` 來接收外部傳進來的值，而這邊又宣告一個 ['name']，表示外部會使用 name 這個變數傳值進來。

`props.name` 就表示接收 name 這個從外部傳進來的變數，然後儲存到 thisName，而這裡儲存的時間點使用 `onMounted` 這個函式的生命週期。

而在這裡又宣告了一個按鈕 `<button @click="sendValue">傳出</button>` ，用意在於這個按鈕按下去時，可以觸發上層，也就是外部的函式，這個稍後會解釋。

所以回到 App.vue，引用這個元件：

```html
<template>
  <Component :name="name" />
</template>

<script>
import { ref } from 'vue'
import Component from './components/Component.vue'

export default {
  name: 'App',
  components: {
    Component,
  },
  setup() {
    const name = ref('Jake');
    
    return {
      name,
    }
  }
}
</script>
```

`<Component :name="name" />` 就表示傳入 name 這個變數給元件。

回到 /components/Component.vue，要如何呼叫外部的函式呢？

```html
<template>
  {{ thisName }}
  <br />
  <button @click="sendValue">傳出</button>
</template>

<script>
export default {
  name: 'Component',
  props: ['name'],
  emits: ['getName'],

  setup(props, context) {
    const thisName = ref('');

    onMounted(() => {
      console.log("onMounted", props.name);
      thisName.value = props.name;
    });

    function sendValue() {
      context.emit('getName', thisName.value);
    }

    return {
      thisName,
      sendValue,
    };
  },
};
</script>
```

按鈕 `<button @click="sendValue">傳出</button>` 按下時會呼叫 sendValue 這個函式，而在 sendValue() 之中，使用 `emit` 將變數回傳出去，這邊回傳出去的變數為 thisName，然後外部必須要用 getName 這個變數來接收。

最後回到 App.vue 修改如下：

```html
<template>
  <Component :name="name" @getName="getName" />
</template>

<script>
import { ref } from 'vue'
import Component from './components/Component.vue'

export default {
  name: 'App',
  components: {
    Component,
  },
  setup() {
    const name = ref('Jake');
    
    function getName(value) {
      alert(value)
    }

    return {
      name,
      getName,
    }
  }
}
</script>
```

`<Component :name="name" @getName="getName" />` 宣告了使用 getName 函式來接收 @getName 這個從元件回傳出來的變數。

然後 getName 這個函式就會接收這個變數，最後使用 alert 來彈跳一個視窗。

```js
function getName(value) {
  alert(value)
}
```

[今日程式碼範例](https://stackblitz.com/edit/vue-7ymfxc?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day26 [完]**