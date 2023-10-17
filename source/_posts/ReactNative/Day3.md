---
title: ReactNative 從零開始學¹ - Day3 - Button
date: 2023-10-17 19:44:32
tags: ReactNative
---

接下來這個單元要來介紹按鈕，而這個按鈕按下去會將數值一直累加 1。

製作按鈕的方式是 `<Button>`，所以在這邊直接放入按鈕：

```js
import { Button, StyleSheet, Text, View } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Button title='Button' />
      <Text>text</Text>
    </View>
  );
}
```

按鈕宣告的方式是 `<Button title='Button' />`，屬性 title 則是按鈕顯示的文字。

接下來宣告一個變數，而這個變數要可以設定數值，會使用到 `useState` 來初始化一個變數：

```js
import { Button, StyleSheet, Text, View } from 'react-native';
import { useState } from 'react';

export default function App() {
  let [count, setCount] = useState(0);

  return (
    <View style={styles.container}>
      <Button title='Button' />
      <Text>{count}</Text>
    </View>
  );
}
```

所以在這邊宣告一個變數 count，由於因為這個變數要可以設定數值進去，所以也必須要宣告 setCount，然後使用 `useState` 來進行初始化，而這裡也必須要引用 `useState`。

而顯示這個變數 count 的方式則必須要用大括號 `{count}`。

接下來要宣告一個函式，按鈕按下去時，會呼叫到這個函式：

```js
const buttonTapped = () => {
  let temp = count;
  temp += 1;
  setCount(temp);
};
```

這個函式裡面的運算，主要就是將 count 進行一個累加 1 的動作，然後使用 setCount 將數值寫入回 count。

而最後按鈕呼叫這個函式的方法則是使用 `onPress`：

```js
<Button title='Button' onPress={buttonTapped} />
```

完整程式碼：

```js
import { Button, StyleSheet, Text, View } from 'react-native';
import { useState } from 'react';

export default function App() {
  let [count, setCount] = useState(0);

  const buttonTapped = () => {
    let temp = count;
    temp += 1;
    setCount(temp);
  };

  return (
    <View style={styles.container}>
      <Button title='Button' onPress={buttonTapped} />
      <Text>{count}</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

最後呈現的效果：

<img src="/images/ReactNative/3_1.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

[本單元完整程式碼範例](https://snack.expo.dev/@mrjk/day3)

<div data-snack-id="@mrjk/day3" data-snack-platform="ios" data-snack-preview="true" data-snack-theme="dark" style="overflow:hidden;background:#0C0D0E;border:1px solid var(--color-border);border-radius:4px;height:505px;width:100%"></div>
<script async src="https://snack.expo.dev/embed.js"></script>

**ReactNative 從零開始學¹ - Day3 [完]**

- 上一篇：[ReactNative 從零開始學¹ - Day2 - Hello World](/ReactNative/Day2)
- 下一篇：[ReactNative 從零開始學¹ - Day4 - ScrollView](/ReactNative/Day4)