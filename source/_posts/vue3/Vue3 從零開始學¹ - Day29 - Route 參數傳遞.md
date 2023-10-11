---
title: Vue3 從零開始學¹ - Day29 - Route 參數傳遞
date: 2023-09-29 08:47:11
tags:
---
這個單元接續上一個單元介紹的 Route 的功能，在 Route 之中，也會希望可以將變數的內容傳到下一頁，例如想要跳轉到 AboutView.vue 時，也傳送資料過去。

修改 App.vue：

```html
<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about?x=aaa">About</router-link>
  </nav>
  <router-view/>
</template>
```

在 about 的網址後面帶入一個 x 等於 aaa，表示宣告一個變數 x 內容是 aaa，所以 /about?x=aaa 就表示將 x 變數的內容傳入給 about 這個路由，這樣傳遞變數的方法稱為 Http Get。

而在 AboutView.vue 就必須要去接收 x 這個變數，使用 this.$route.query.x 來接收，修改 AboutView.vue：

```html
<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h1>{{ x }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      x: this.$route.query.x
    }
  }
}
</script>
```

所以這邊使用 `this.$route.query` 並且加入變數 x，就表示接收來自網址的 x 變數的內容，然後給予變數 x。

所以當跳轉到 about 時，就會顯示 x 這個變數的內容：

![https://ithelp.ithome.com.tw/upload/images/20230913/20162607isvAfgjbzR.png](https://ithelp.ithome.com.tw/upload/images/20230913/20162607isvAfgjbzR.png)

上述的寫法是使用 Option API 的方式，如果要使用 Composition API，修改 App.vue：

```html
<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link :to="{ path: '/about', query: { y: 'yyyy' } }">
      About
    </router-link>
  </nav>
  <router-view />
</template>
```

在這裡一樣使用 `<router-link>` 指定兩個變數 path: '/about' 與 query: { y: 'yyyy' }，path就是要轉址的位置，query 就是傳遞參數的內容，這裡也可以指定多個參數：

```html
<router-link :to="{ path: '/about', query: { y: 'yyyy', x: 'xxxx' } }">
  About
</router-link>
```

而在 AboutView.vue 就必須要去接收 x 這個變數，使用 `getCurrentInstance` 來接收，修改 AboutView.vue：

```html
<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h1>{{ y }}</h1>
  </div>
</template>

<script>
import { ref, onMounted, getCurrentInstance } from "vue";

export default {
  setup() {
    let y = ref('');

    onMounted(() => {
      const instance = getCurrentInstance();
      y.value = instance.proxy.$route.query.y;
    });

    return {
      y
    };
  }
}
</script>
```

在這裡引用了 `getCurrentInstance` ，並且宣告 `const instance = getCurrentInstance();`，然後在 instance 呼叫 `proxy.$route.query` ，並且帶入變數名稱 y，就可以取得到 y 的內容。

[今日程式碼範例](https://stackblitz.com/edit/vue-gkacwf?file=src%2Fviews%2FAboutView.vue)

**Vue3 從零開始學¹ - Day29 [完]**
