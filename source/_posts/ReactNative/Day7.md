---
title: ReactNative 從零開始學¹ - Day7 - Alert
date: 2023-10-24 12:17:18
tags:
---

這個單元要來討論 `Alert` 警告視窗的做法。

首先先引入 `Alert` 這個元件，而一個最簡單的，使用 `Alert` 的方式為直接呼叫 `Alert.alert`：

```js
import { Button, StyleSheet, View, Alert } from 'react-native';

export default function App() {
  const buttonTapped = () => {
    Alert.alert("Hello Alert!");
  };

  return (
    <View style={styles.container}>
      <Button title="button" color='red' onPress={buttonTapped} />
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

而這裡是利用一個按鈕 `Button` 按下去時，會去呼叫 `Alert.alert`，帶入一個參數為字串，表示這個警告視窗所顯示的標題內容。

<img src="/images/ReactNative/7_1.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

Alert 可以有多個輸入參數，例如第二個一樣輸入字串，則可以顯示 Alert 的內文：

```js
Alert.alert("Hello Alert!", "Alert 要放的內容");
```

模擬器顯示：

<img src="/images/ReactNative/7_2.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

Alert 的第三個參數，是輸入陣列，則可以顯示 Alert 的按鈕：

```js
Alert.alert("Hello Alert!", "Alert 要放的內容", [{
  text: 'OK',
  onPress: ()=> console.log('OK Tapped')
}]);
```

這裡帶入的第三個參數是一個陣列，陣列元素使用物件帶入，裡面有兩個參數 `text` 與 `onPress`，分別表示按鈕的顯示文字與按鈕按下時觸發的事件。

所以這個陣列可以帶入第二個元素，一樣使用 `text` 與 `onPress` 所包成的物件帶入：

```js
Alert.alert("Hello Alert!", "Alert 要放的內容", [{
  text: 'OK',
  onPress: () => console.log('OK Tapped')
}, {
  text: 'Cancel',
  onPress: () => console.log('Cancel Tapped')
}]);
```

模擬器顯示：

<img src="/images/ReactNative/7_3.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

[本單元完整程式碼範例](https://snack.expo.dev/@mrjk/day7---alert)

<div data-snack-id="@mrjk/day7---alert" data-snack-platform="ios" data-snack-preview="true" data-snack-theme="dark" style="overflow:hidden;background:#0C0D0E;border:1px solid var(--color-border);border-radius:4px;height:505px;width:100%"></div>
<script async src="https://snack.expo.dev/embed.js"></script>

**ReactNative 從零開始學¹ - Day7 [完]**

- 上一篇：[ReactNative 從零開始學¹ - Day6 - Modal](/ReactNative/Day6)
- 下一篇：[ReactNative 從零開始學¹ - Day8 - ActivityIndicator](/ReactNative/Day8)
