---
title: Vue3 從零開始學¹ - Day3 - Hello World
date: 2023-09-03 11:00:44
tags:
---

在上一個單元，已經學會了基本的 Vue3 程式流程，接下來將會開始探討一些最基礎的知識，就如往常學習其它程式語言一樣，從 Hello World 開始。

接下來的所有基本範例，都會從修改 App.vue 開始，所以勇敢的把所有程式碼刪除掉吧。開啟 App.vue ，然後刪除所有的程式碼，在這裡 `<style></style>` 可以根據自己的喜好選擇要不要刪除，`<style></style>` 標籤只會跟網頁排版有關係而已，留不留都無所謂，不會影響到程式流程，為了文章的說明簡潔，所以這邊以下的所有程式碼範例都不會說明 `<style></style>` 標籤。

將 App.vue 所有程式碼刪除掉，只留下 `<template></template>` 與 `<script></script>`：

```javascript
<template>
 
</template>

<script>

</script>
```

但這個時候如果切換到網頁時，會產生錯誤訊息：

![https://ithelp.ithome.com.tw/upload/images/20230903/20162607CIjn5OSGTT.png](https://ithelp.ithome.com.tw/upload/images/20230903/20162607CIjn5OSGTT.png)

如果切換到終端機時，也會看到以下錯誤：

```
ERROR  Failed to compile with 1 error                                                                                             上午10:28:30

[eslint]
/Users/jake/Desktop/vue3-demo/src/App.vue
  1:1  error  The template requires child element  vue/valid-template-root

✖ 1 problem (1 error, 0 warnings)


You may use special comments to disable some warnings.
Use // eslint-disable-next-line to ignore the next line.
Use /* eslint-disable */ to ignore all warnings in a file.
ERROR in [eslint]
/Users/jake/Desktop/vue3-demo/src/App.vue
  1:1  error  The template requires child element  vue/valid-template-root

✖ 1 problem (1 error, 0 warnings)


webpack compiled with 1 error
```

因為 Vue3 不允許宣告了 `<template></template>` 與 `<script></script>` 這兩個標籤，而不寫任何 html 標籤或者程式邏輯。

然後在 `<script></script>` 內，改寫成：

```javascript
<script>
export default {
  name: 'App',
  data() {
    return {
      message: 'Hello World',
    };
  },
};
</script>
```

雖然 Vue3 的程式語法是使用 Javascript，習慣使用 jQuery 開發的朋友，看到這段程式碼一開始一定無法適應，沒關係，我一行一行來解釋。

第2行：所有程式邏輯都必須要寫在 `export default {}` 裡頭。
第3行：`name: 'App'` 宣告這個 .vue 的名稱。
第4行：`data() {}` 是宣告變數的地方，在裡面使用 `return` 來輸出一個變數 `message`，輸出的意思就是將變數輸出給 `<template></template>` 可以來使用。而這個變數 `message` 的型別是一個字串，給予了 `'Hello World'`。

而要把這個變數 message 顯示在 `<template></template>` 內的話，就必須要使用雙層大括號 `{{ message }}`。

```javascript
<template>
  {{ message }}
</template>
```

如此一來就可以在網頁上看到 Hello World 了。

![https://ithelp.ithome.com.tw/upload/images/20230903/20162607Ni7RcOzRkT.png](https://ithelp.ithome.com.tw/upload/images/20230903/20162607Ni7RcOzRkT.png)

所有程式碼：

```javascript
<template>
  {{ message }}
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      message: 'Hello World',
    };
  },
};
</script>
```

所以這段程式碼簡單的說，宣告了一個變數 `message`，型別是字串，給予 `'Hello World'`，然後顯示在網頁上。

[本日範例程式碼參考](https://stackblitz.com/edit/vue-rtyurf?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day3 [完]**