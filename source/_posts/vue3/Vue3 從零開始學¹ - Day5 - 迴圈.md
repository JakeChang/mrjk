---
title: Vue3 從零開始學¹ - Day5 - 迴圈
date: 2023-09-05 18:30:11
tags:
---

在上一個單元，已經學習到如何使用 `if` 判斷式，接下來這個單元進入到迴圈。`if` 判斷式可以方便使用變數來控制內容是否顯示，而迴圈則是方便顯示重複的內容。

迴圈通常會跟陣列一起使用，先宣告一個陣列變數：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      users1: ['Jake', 'Allan', 'Eason'],
    };
  },
};
</script>
```

宣告了一個陣列 user1，然後放入三個字串，陣列的意思是說將這三個字串放在一個有序列功能的變數裡面，這個變數就是 user1，可以只透過 user1 來存取這三個字串，而不需要重複宣告三個變數來放這三個字串。

跟 `v-if` 類似，迴圈是使用 `v-for` 來表示：

```html
<template>
  <p v-for="user in users1" :key="user">{{ user }}</p>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      users1: ['Jake', 'Allan', 'Eason'],
    };
  },
};
</script>
```

宣告了一個陣列 user1，放入三個字串，在 `<template></template>` 使用 `v-for` 來走訪陣列的所有元素，使用 `user in users1` 語法定義了另外一個變數 user，就是用來走訪陣列 users1 的所有元素，所以這個變數 user 就可以使用 `{{ user }}` 來顯示。

迴圈還可以透過 index 變數來表示資料的編號：

```html
<template>
  <p v-for="(user, index) in users1" :key="user">{{ index }} {{ user }}</p>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      users1: ['Jake', 'Allan', 'Eason'],
    };
  },
};
</script>
```

但這樣的陣列有時候不能滿足某些需求，例如除了名字之外，還需要將每個人的 email 一起對應，這個時候就會需要使用物件陣列：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      users2: [
        { name: 'Jake', email: 'jake@gmail.com' },
        { name: 'Allan', email: 'allan@gmail.com' },
        { name: 'Eason', email: 'eason@gmail.com' },
      ],
    };
  },
};
</script>
```

物件陣列內的元素必須要用 `{}` 包起來，然後必須要指定 key，例如 `name: 'Jake'`，就表示宣告一個變數 name 等於 Jake。`email: 'jake@gmail.com'`，就表示宣告一個變數 email 等於 jake@gmail.com。所以這邊的 name 跟 email 就是指定的 key。

然後就可以很方便的使用迴圈來直接存取這兩個 key：

```html
<template>
  <p v-for="(user, index) in users2" :key="user.email">
    {{ index }} {{ user.name }} {{ user.email }}
  </p>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      users2: [
        { name: 'Jake', email: 'jake@gmail.com' },
        { name: 'Allan', email: 'allan@gmail.com' },
        { name: 'Eason', email: 'eason@gmail.com' },
      ],
    };
  },
};
</script>
```

因為變數 user 會走訪陣列 user2 的每一個元素，就可以直接使用變數 user 來指定 key，存取 name 與 email 了。

最後將上一個單元學到的 v-if 判斷，加入到迴圈判斷：

```html
<template>
  <div v-for="(user, index) in users1" :key="user">
    <p v-if="user === 'Jake'">{{ index }} {{ user }}</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      users1: ['Jake', 'Allan', 'Eason'],
    };
  },
};
</script>
```

user 這個變數走訪陣列 user1，然後經過 if 判斷是否會等於 Jake，如果等於 Jake 才會顯出其內容。

[今日程式碼範例](https://stackblitz.com/edit/vue-8ipjtz?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day5 [完]**