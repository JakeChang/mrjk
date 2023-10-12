---
title: Vue3 從零開始學¹ - Day7 - Demo
date: 2023-09-07 12:35:20
tags:
---

在經歷過一週的基礎洗禮之後，想必是想摩拳擦掌，好好大展身手了。

這個單元會有一個實際的例子，在這個例子，會有一個按鈕，按下這個按鈕之後，會把數值加上 1，就是這麼簡單的一個範例，但是完成之後也會有相當程度的成就感，因為是把過去幾天的學習好好融會貫通而已。

首先第一步，先宣告一個變數 count，初始值為 0：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0,
    };
  },
};
</script>
```

接下來將上一個單元學到的宣告函式的方法，宣告一個函式：

```html
<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    myFunction() {
    },
  },
};
</script>
```

這個函式的名稱我宣告為 myFunction，一樣可以自由命名想要的名稱。

因為會希望每次呼叫這個函式時，都會將數值加上 1，所以改寫這個函式：

```javascript
methods: {
  myFunction() {
    this.count += 1;
  },
},
```

`this.count += 1;` 這樣的寫法會等於：

```javascript
this.count = this.count + 1;
```

簡單講就是每次呼叫都把 count 加上 1，並且存入回原本的 count。

接下來在 `<template></template>` 放入這個 count 變數與一個按鈕：

```html
<template>
  {{ count }}
  <button>button</button>
</template>
```

將按鈕按下去時，要去呼叫 myFunction 這個函式，在 Vue3 呼叫函式的方法會使用 `v-on:click` 這個方式，所以 html 可以改寫成：

```html
<template>
  {{ count }}
  <button v-on:click="myFunction">button</button>
</template>
```

如此一來，按鈕按下去時，會將 count 加上 1，而且顯示出來，所有的程式碼：

```html
<template>
  {{ count }}
  <button v-on:click="myFunction">button</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    myFunction() {
      this.count += 1;
    },
  },
};
</script>
```

`v-on:click` 這個寫法，可以省略用 `@click` 來取代：

```html
<template>
  {{ count }}
  <button @click="myFunction">button</button>
</template>
```

此外，呼叫函式的時候，也可以將數值傳給函式：

```html
<template>
  {{ count }}
  <button @click="myFunction(10)">button</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    myFunction(temp) {
      this.count += temp;
    },
  },
};
</script>
```

在這個例子，每次按鈕按下時，都會把 10 傳給 myFunction ，所以每次都會把 count 變數加上 10。

最後，每次呼叫函式時，也可以一次呼叫多個函式，所以在這邊多宣告了一個函式 changeName：

```html
<template>
  {{ name }}
  {{ count }}
  <button @click="myFunction(), changeName()">button</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0,
      name: 'Jake',
    };
  },
  methods: {
    myFunction() {
      this.count += 1;
    },
    changeName() {
      this.name = 'Allan';
    },
  },
};
</script>
```

[今日程式碼範例](https://stackblitz.com/edit/vue-gdhpbc?file=src%2FApp.vue)

### 一週挑戰後記

終於完成 7 日挑戰，原本對於寫這種技術文章不是很熱衷的我，最大的感想是，對於技術的說明會越來越有著力點，會比較知道要如何去說明與講解技術，而此外寫文章是一種重複的複習，寫完一遍，是第一遍，寫完重看，是第二遍，寫完要發表前再度檢視，是第三遍，雖然會花上很多時間，但對自己只有好處沒有壞處，唯一的壞處就是時間不見了。

關於學習新技術與如何吸收，之後有空再來寫一篇我的觀點。

**Vue3 從零開始學¹ - Day7 [完]**
