---
title: Vue3 從零開始學¹ - Day18 - 製作 Tab 瀏覽
date: 2023-09-18 09:27:29
tags:
---
元件大致上的使用規則都已經了解後，這一個單元會實際用一個例子來講解元件的其中一個用法，就是可以使用元件來製作 Tab 的瀏覽方式。

一開始先新增三個元件檔案，分別是 components/Component1.vue：

```html
<template>
  <p>Component1</p>
</template>

<script>
export default {
  name: 'Component1',
};
</script>
```

components/Component2.vue：

```html
<template>
  <p>Component2</p>
</template>

<script>
export default {
  name: 'Component2',
};
</script>
```

components/Component3.vue：

```html
<template>
  <p>Component3</p>
</template>

<script>
export default {
  name: 'Component3',
};
</script>
```

在上層檔案 App.vue 引用這三個元件：

```html
<template>
</template>

<script>
import Component1 from './components/Component1.vue';
import Component2 from './components/Component2.vue';
import Component3 from './components/Component3.vue';

export default {
  name: 'App',
  components: {
    Component1,
    Component2,
    Component3,
  },
};
</script>
```

然後在 `<template></template>` 內宣告三個按鈕與這三個元件：

```html
<template>
  <button>Component1</button>
  <button >Component2</button>
  <button>Component3</button>

  <Component1 />
  <Component2 />
  <Component3 />
</template>
```

所以目前的畫面上，就會同時顯示這三個按鈕與三個元件的內容。

這邊的功能會需要當按鈕按下時，才會根據按下哪一個按鈕顯示對應的元件，所以必須要新增函式來實現這個功能：

```html
<template>
  <button @click="show('tab1')">Component1</button>
  <button @click="show('tab2')">Component2</button>
  <button @click="show('tab3')">Component3</button>

  <Component1 />
  <Component2 />
  <Component3 />
</template>

<script>
import Component1 from './components/Component1.vue';
import Component2 from './components/Component2.vue';
import Component3 from './components/Component3.vue';

export default {
  name: 'App',
  components: {
    Component1,
    Component2,
    Component3,
  },
  data() {
    return {
      tab: 'tab1',
    };
  },
  methods: {
    show(index) {
      this.tab = index;
    },
  },
};
</script>
```

所以這邊宣告了一個變數 tab，初始值為 tab1。按鈕按下會呼叫 show 這個函式，然後帶入參數會去更新變數 tab。

這樣還不夠，當變數 tab 被更新時，這三個元件也要根據變數 tab 來顯示或者消失，所以使用 `v-if` 來實現這個功能：

```html
<template>
  <button @click="show('tab1')">Component1</button>
  <button @click="show('tab2')">Component2</button>
  <button @click="show('tab3')">Component3</button>

  <Component1 v-if="tab === 'tab1'" />
  <Component2 v-if="tab === 'tab2'" />
  <Component3 v-if="tab === 'tab3'" />
</template>

<script>
import Component1 from './components/Component1.vue';
import Component2 from './components/Component2.vue';
import Component3 from './components/Component3.vue';

export default {
  name: 'App',
  components: {
    Component1,
    Component2,
    Component3,
  },
  data() {
    return {
      tab: 'tab1',
    };
  },
  methods: {
    show(index) {
      this.tab = index;
    },
  },
};
</script>
```

如此一來就完成一個基本的使用按鈕來切換頁面的效果。

這個時候如果去修改某一個元件：

```html
<template>
  <p>Component3</p>
  <input type="text" />
</template>

<script>
export default {
  name: 'Component3',
};
</script>
```

當切換這個按鈕去輸入內容到 input 時，然後又切換到另外一個 Component1 或者 Component2，當再度切換到 Component3 時，會發現這個 input 的內容會被清空。

所以這邊如果要實現元件不會被清空，就要使用 keep alive 來實現：

```html
<template>
  <button @click="show('tab1')">Component1</button>
  <button @click="show('tab2')">Component2</button>
  <button @click="show('tab3')">Component3</button>

  <Component1 v-if="tab === 'tab1'" />
  <Component2 v-if="tab === 'tab2'" />

  <keep-alive>
    <Component3 v-if="tab === 'tab3'" />
  </keep-alive>
</template>

<script>
import Component1 from './components/Component1.vue';
import Component2 from './components/Component2.vue';
import Component3 from './components/Component3.vue';

export default {
  name: 'App',
  components: {
    Component1,
    Component2,
    Component3,
  },
  data() {
    return {
      tab: 'tab1',
    };
  },
  methods: {
    show(index) {
      this.tab = index;
    },
  },
};
</script>
```

這邊在 Component3 的上層多加了 `<keep-alive>` 標籤就可以保留元件內的輸入內容了。

[今日程式碼範例](https://stackblitz.com/edit/vue-mu3rbs?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day18 [完]**