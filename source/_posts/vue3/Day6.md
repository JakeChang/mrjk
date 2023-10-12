---
title: Vue3 從零開始學¹ - Day6 - 函式
date: 2023-09-06 12:20:23
tags:
---

前兩個單元已經學會了 if 判斷式與迴圈，接下來討論在程式語言之中最常用的函式。

首先，先宣告兩個變數 x 跟 y，型別都是數字：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      x: 100,
      y: 2,
    };
  },
};
</script>
```

如果要將 x 跟 y 兩個變數做數學運算，例如相乘，可以這樣寫：

```html
<template>
  {{ x * y }}
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      x: 100,
      y: 2,
    };
  },
};
</script>
```

但是如果這兩個變數相乘的數學運算會用在兩個地方，這樣是一種寫法：

```html
<template>
  {{ x * y }}
  <br>
  {{ x * y }}
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      x: 100,
      y: 2,
    };
  },
};
</script>
```

有沒有發現什麼問題？如果需要用這套數學運算在 10 個地方呢？會需要寫 10 次，又如果這個相乘的運算要修改成相加，是不是又要改 10 次？

其實不用這麼麻煩，函式在這個時候就派上用場，在 Vue3 要使用函式，必須要使用 `methods: {}` 來宣告函式，宣告一個函式的寫法：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      x: 100,
      y: 2,
    };
  },
  methods: {
    myFunction() {
      return this.x * this.y;
      //注意在這邊要用 this 來取得定義在 data() 內的變數
    },
  },
};
</script>
```

函式的寫法必須要使用一個名稱，在這邊命名為 myFunction，而這個 myFunction 內部直接回傳 x 跟 y 的相乘結果，這邊要注意用 `this` 來取得定義在 `data()` 內的兩個變數 x 跟 y。

所以在 <template></template> 內就可以直接呼叫這個函式的名稱：

```html
<template>
  {{ myFunction() }}
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      x: 100,
      y: 2,
    };
  },
  methods: {
    myFunction() {
      return this.x * this.y;
    },
  },
};
</script>
```

呼叫 10 次也不怕了：

```html
<template>
  {{ myFunction() }} <br>
  {{ myFunction() }} <br>
  {{ myFunction() }} <br>
  {{ myFunction() }} <br>
  {{ myFunction() }} <br>
  {{ myFunction() }} <br>
  {{ myFunction() }} <br>
  {{ myFunction() }} <br>
  {{ myFunction() }} <br>
  {{ myFunction() }}
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      x: 100,
      y: 2,
    };
  },
  methods: {
    myFunction() {
      return this.x * this.y;
    },
  },
};
</script>
```

最後，函式還可以將某一個值傳給函式來使用：

```html
<template>
  {{ myFunction(100) }}
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      x: 100,
      y: 2,
    };
  },
  methods: {
    myFunction: function (value) {
      return this.x * this.y + value;
    },
  },
};
</script>
```

在這邊傳入一個數值 100 給 myFunction，然後與 x 跟 y 的相乘結果相加起來。所以在這邊的例子會印出 300。

[今日程式碼範例](https://stackblitz.com/edit/vue-mklzcm?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day6 [完]**