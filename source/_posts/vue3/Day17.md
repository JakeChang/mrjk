---
title: Vue3 從零開始學¹ - Day17 - 元件 slot
date: 2023-09-17 08:50:11
tags:
---
元件可以幫助我們將一些共用的畫面來切割並且可以重複使用，讓維護成本降低，但是有得時候雖然使用了元件，但還是會需要一些畫面的微調。

這個單元就要來介紹可以傳入 html 標籤給元件的方法，slot。使用 slot 可以讓上層傳入 html 標籤。

新增一個元件檔案 components/Card.vue：

```html
<template>
  <div>
    <!-- 使用 slot 可以讓外部 HTML 傳入 -->
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'Input'
};
</script>
```

然後在上層的 App.vue 引用這個元件時，就可以傳入 html 相關標籤：

```html
<template>
  <Card>
    <h2>Content</h2>
  </Card>
</template>

<script>
import Card from './components/Card.vue';

export default {
  name: 'App',
  components: {
    Card,
  },
};
</script>
```

在這裡傳入 `<h2>` 標籤，元件就會顯示這個 `<h2>` 標籤。

也可以傳入連結標籤 `<a>`：

```html
<template>
  <Card>
    <h2>Content</h2>
  </Card>
  <Card>
    <a href="">Link</a>
  </Card>
</template>

<script>
import Card from './components/Card.vue';

export default {
  name: 'App',
  components: {
    Card,
  },
};
</script>
```

也可以指定某一個 slot 來傳入 html 標籤：

```html
<template>
  <div>
    <slot name="header">header</slot>
    <slot name="content">content</slot>
  </div>
</template>

<script>
export default {
  name: 'Input',
};
</script>
```

slot 帶入 name 就可以宣告這一個 slot 的名稱。

然後上層就可以指定要用哪一個 slot 來取代：

```html
<template>
  <Card>
    <template v-slot:header>
      <h1>My Header</h1>
    </template>
  </Card>
</template>

<script>
import Card from './components/Card.vue';

export default {
  name: 'App',
  components: {
    Card,
  },
};
</script>
```

使用 `<template v-slot:header></template>` 表示指定元件內的 slot 名稱為 header 。

[今日程式碼範例](https://stackblitz.com/edit/vue-2us8fh?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day17 [完]**