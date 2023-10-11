---
title: Vue3 從零開始學¹ - Day24 - Composition 監聽
date: 2023-09-24 10:44:53
tags:
---
這個單元繼續討論 Composition API，在變數的監聽上與 Option API 有什麼不一樣？

宣告 `ref` 變數：

```html
<template>
  <input type="text" v-model="name" />
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'App',
  setup() {
    const name = ref('Jake');

    return {
      name,
    };
  },
};
</script>
```

如果要針對變數 name 來進行監聽時，修改如下：

```html
<template>
  <input type="text" v-model="name" />
</template>

<script>
import { ref, watch } from 'vue';

export default {
  name: 'App',
  setup() {
    const name = ref('Jake');

    watch(name, (newValue, oldValue) => {
       console.log(newValue, oldValue);
    });

    return {
      name,
    };
  },
};
</script>
```

引用 `watch` ，直接輸入要監聽的變數名稱，就可以得到監聽時的變數變化，newValue 表示監聽到最新到值，oldValue 表示監聽到最新的值的前一個值。

那如果要監聽好幾個變數，是不是就會需要寫好幾個 watch？其實不用這麼麻煩，可以使用多個變數的監聽方式：

```html
<template>
  <input type="text" v-model="name" />
  <input type="text" v-model="email" />
</template>

<script>
import { ref, watch } from 'vue';

export default {
  name: 'App',
  setup() {
    const name = ref('Jake');
    const email = ref('');
 
    watch(
      [name, email],
      (newValue, oldValue) => {
        console.log('name', newValue[0], oldValue[0]);
        console.log('email', newValue[1], oldValue[1]);
      },
      {
        immediate: true, //如果變數一開始有值，就會被 watch
      }
    );

    return {
      name, email,
    };
  },
};
</script>
```

一樣使用 `watch` ，帶入一個陣列，這個陣列將要監聽的變數通通帶入，newValue 與 oldValue 會回傳陣列，指定陣列的位址可以得到相對應的變數，如 newValue[0] 與 oldValue[0] 是變數 name，newValue[1] 與 oldValue[1] 是變數 email。

如果是宣告 `reactive` 變數：

```html
<template>
  <input type="text" v-model="phone" />
</template>

<script>
import { reactive, watch, toRefs } from 'vue';

export default {
  name: 'App',
  setup() {
    const user = reactive({
      phone: '',
    });
    
    watch(
      () => {
        return { ...user };
      },
      (newValue, oldValue) => {
        console.log('user', newValue.phone, oldValue.phone);
      }
    );

    return {
      ...toRefs(user),
    };
  },
};
</script>
```

這裡的 `watch` 寫法稍微不一樣，使用 () => { return {}; } 將要監聽的 `reactive` 變數傳入，就可以在 newValue 與 oldValue 直接指定 phone 這個變數了。

[今日程式碼範例](https://stackblitz.com/edit/vue-i8ffoh?file=src%2FApp.vue)

**Vue3 從零開始學¹ - Day24 [完]**