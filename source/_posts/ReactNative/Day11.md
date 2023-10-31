---
title: ReactNative 從零開始學¹ - Day11 - alignItems
date: 2023-10-31 18:56:56
tags: ReactNative
---

這單元繼續討論排版， `flex` 可以幫助設定切割版面的大小，而 `justifyContent` 可以設定垂直方向的位置，那麼還缺少水平位置的排版，`alignItems` 就是可以針對水平位置排版的屬性。

首先延續上一個單元的範例，宣告三個 box ，但這邊不一樣的是把 width 拿掉：

```js
import { StyleSheet, View, Text } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <View style={[styles.box, { backgroundColor: 'red' }]}><Text>Box1</Text></View>
      <View style={[styles.box, { backgroundColor: 'blue' }]}><Text>Box2</Text></View>
      <View style={[styles.box, { backgroundColor: 'gray' }]}><Text>Box3</Text></View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    margin: 44,
  },
  box: {
    height: 50,
  }
});
```

開啟模擬器會呈現：

<img src="/images/ReactNative/11_1.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

接下來加入 `alignItems` 屬性 並且設定 `stretch`：

```css
container: {
  flex: 1,
  margin: 44,
  alignItems: 'stretch',
},
```

stretch 是初始的屬性，就算不設定，也是會呈現如上圖模擬器的樣貌。

而 alignItems 一共有 `stretch`、`flex-start`、`flex-end`、`center`、`baseline` 五種屬性可以設定。

`flex-start` 是針對水平位置左邊對齊：

<img src="/images/ReactNative/11_2.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

`flex-end` 是針對水平位置右邊對齊：

<img src="/images/ReactNative/11_3.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

`center` 是針對水平位置中間對齊：

<img src="/images/ReactNative/11_4.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

**ReactNative 從零開始學¹ - Day11 [完]**

- 上一篇：[ReactNative 從零開始學¹ - Day10 - justifyContent](/ReactNative/Day10)
- 下一篇：