---
title: Vue3 從零開始學¹ - Day21 - Composition
date: 2023-09-21 07:05:32
tags:
---
呼～

我們花了 20 天來介紹 Vue3 的最基礎語法，在前面 20 天介紹的 Vue3 語法稱為 Options API，接下來幾天會介紹另外一種語法稱為 Composition API。

看到這裡你一定也會心中出現大大問號，好好的一個 Vue3 為何要搞分裂，要出兩種語法 API ?
 
其實 Composition API 的出現也是為了要解決 Options API 寫到後期可能會出現的語法複雜度，以及不容易閱讀，還有元件的重複使用度等問題。

我在這裡先不評斷兩種 API 的好處與壞處，先慢慢了解 Composition API 到底是怎麼一回事？最後再來分析評斷。

所以時光倒轉，回到第三天重新學習宣告變數，這次是使用 Vue3 的 Composition 來宣告。

### 宣告變數

```html
<template>
  {{ name }}
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'App',
  setup() {
    const name = ref('');
    return {
      name,
    };
  },
};
</script>
```

使用 Composition 宣告變數要用 ref 來初始化，而這個 ref 必須要先 import 才可以使用。

所以一開始 `import { ref } from 'vue';` 引用 ref 來使用。

使用 `setup() {}` 把變數放在此內部。

使用 `const name = ref('');` 來進行變數的宣告，並且用 ref 來初始化這個變數為空白。

如果要修改這個變數的話，要使用 .value：

```html
<template>
  {{ name }}
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'App',
  setup() {
    const name = ref('');
    
    //設定值要使用 value
    name.value = 'Jake';
    
    return {
      name,
    };
  },
};
```

### 宣告結構變數

```html
<template>
  {{ user.id }} {{ user.name }}
</template>

<script>
import { reactive } from 'vue';

export default {
  name: 'App',
  setup() {
    const user = reactive({
      id: 0,
      name: '',
    });
    return {
      user,
    };
  },
};
</script>
```

如果要宣告結構變數的話就必須要使用 reactive ，然後將變數放在裡面，而初始化的時候就不用 ref 了。而這個 reactive 也必須要 import 才可以使用。

而如果要修改結構變數的話：

```html
<template>
  {{ user.id }} {{ user.name }}
</template>

<script>
import { reactive } from 'vue';

export default {
  name: 'App',
  setup() {
    const user = reactive({
      id: 0,
      name: '',
    });

    user.id = 1;
    user.name = 'Allan';

    return {
      user,
    };
  },
};
</script>
```

reactive 設定值就不需要使用 value 了。

[今日程式碼範例](https://stackblitz.com/edit/vue-hyr8hr?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day21 [完]**