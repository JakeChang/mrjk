---
title: ReactNative 從零開始學¹ - Day4 - Button
date: 2023-10-17 22:10:20
tags: ReactNative
---

這個單元繼續來討論 Button，一個最簡單的按鈕使用方式：

```js
import { Button, StyleSheet, View } from 'react-native';

export default function App() {
  const buttonTapped = () => {
    console.log('buttonTapped');
  };

  return (
    <View style={styles.container}>
      <Button title="button" onPress={buttonTapped} />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
    padding: 24,
  },
});
```

按鈕宣告使用 `Button`，屬性 `title` 宣告按鈕名稱，`onPress` 宣告按鈕的函式。

`color` 可以改變按鈕的顏色：

```js
<Button title="button" color='red' onPress={buttonTapped} />
```

`disabled` 可以使按鈕失效無法按下：

```js
<Button title="button" color='red' onPress={buttonTapped} disabled/>
```

此外，如果是非按鈕形式的 UI 元件，則必須要使用 `Pressable` 來產生按鈕的觸發狀態：

```js
import { Button, StyleSheet, View, Text, Pressable } from 'react-native';

export default function App() {
  const buttonTapped = () => {
    console.log('buttonTapped');
  };

  return (
    <View style={styles.container}>
      <Pressable onl={buttonTapped}>
        <Text>Hello World!</Text>
      </Pressable>

      <Button title="button" color='red' onPress={buttonTapped} disabled />
    </View>
  );
}
```

這裡宣告了一組 `<Text>`，由於 `<Text>` 是沒有按鈕的觸發狀態，所以在外層包了一個 `Pressable` 來呼叫函式。

最後，除了 `onPress` 的觸發狀態之外，還有 `onLongPress` 表示長案時觸發：

```js
<Pressable onLongPress={buttonTapped}>
  <Text>Hello World!</Text>
</Pressable>
```

`onPressIn` 表示按下時觸發：

```js
<Pressable onPressIn={buttonTapped}>
  <Text>Hello World!</Text>
</Pressable>
```

`onPressOut` 表示按下並且放開時觸發：

```js
<Pressable onPressOut={buttonTapped}>
  <Text>Hello World!</Text>
</Pressable>
```

<div data-snack-id="@mrjk/71eb17" data-snack-platform="web" data-snack-preview="true" data-snack-theme="dark" style="overflow:hidden;background:#0C0D0E;border:1px solid var(--color-border);border-radius:4px;height:505px;width:100%"></div>
<script async src="https://snack.expo.dev/embed.js"></script>

[本單元完整程式碼範例](https://snack.expo.dev/@mrjk/day4---button)

**ReactNative 從零開始學¹ - Day4 [完]**

- 上一篇：[ReactNative 從零開始學¹ - Day3 - Button](/ReactNative/Day3)
- 下一篇：[ReactNative 從零開始學¹ - Day5 - ScrollView](/ReactNative/Day5)