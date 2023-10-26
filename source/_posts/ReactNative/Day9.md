---
title: ReactNative 從零開始學¹ - Day9 - Style Flex
date: 2023-10-26 12:31:47
tags: ReactNative
---

這個單元開始要來討論排版，不管是開發 App 或者 Web，前端最重要的事情就是切版，也就是要如將整個版面切割成不同大小，然後放置 UI，而 `flex` 就是用來切割版面的屬性。

首先一開始先宣告三個 `View` 元件，裡面分別放入三個字串：

```js
import { StyleSheet, View, Text } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <View><Text>Box1</Text></View>
      <View><Text>Box2</Text></View>
      <View><Text>Box3</Text></View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    margin: 24,
  },
});
```

目前版面相當當純，會呈現這個樣子：

<img src="/images/ReactNative/9_0.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

而在 `style` 的宣告方式除了可以使用 `StyleSheet.create` 之外，也可以直接在 UI 元件內宣告：

```js
<View style={styles.container}>
  <View style={{ flex: 1, backgroundColor: 'red' }}><Text>Box1</Text></View>
  <View ><Text>Box2</Text></View>
  <View><Text>Box3</Text></View>
</View>
```

這裡直接在 `View` 元件內宣告 `style`，然後設定兩種屬性 `flex` 與 `backgroundColor`。

剛剛有提到 `flex` 是用來切割版面用的，會直接帶入數字，這邊帶入數字 1 ，表示會佔滿整個版面，所以會呈現這個樣子：

<img src="/images/ReactNative/9_1.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

而因為下方還有兩個 `View` 元件，因為這兩個 `View` 元件沒有宣告 `flex` 樣式，所以會被擠壓到最下面。

如果把這三個 `View` 元件通通宣告 `flex` 屬性，並且都是設定數字 1：

```js
<View style={styles.container}>
  <View style={{ flex: 1, backgroundColor: 'red' }}><Text>Box1</Text></View>
  <View style={{ flex: 1, backgroundColor: 'blue' }}><Text>Box2</Text></View>
  <View style={{ flex: 1, backgroundColor: 'gray' }}><Text>Box3</Text></View>
</View>
```

就表示 `flex` 總數會等於 3，而每一個 `View` 元件的 `flex` 為 1，所以每一個 `View` 會佔滿 1/3 個版面：

<img src="/images/ReactNative/9_2.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

又例如將第二個 `View` 元件的 `flex` 設定為 2：

```js
<View style={styles.container}>
  <View style={{ flex: 1, backgroundColor: 'red' }}><Text>Box1</Text></View>
  <View style={{ flex: 2, backgroundColor: 'blue' }}><Text>Box2</Text></View>
  <View style={{ flex: 1, backgroundColor: 'gray' }}><Text>Box3</Text></View>
</View>
```

就表示 `flex` 總數會等於 4，而第一個與第三個 `View` 的 `flex` 為 1，所以會佔滿 1/4 個版面，而第二個 `View` 會佔滿 2/4：

<img src="/images/ReactNative/9_3.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

又例如將第二個 `View` 的 `flex` 設定為 2，第三個 `View` 的 `flex` 設定為 3：

```js
    <View style={styles.container}>
      <View style={{ flex: 1, backgroundColor: 'red' }}><Text>Box1</Text></View>
      <View style={{ flex: 2, backgroundColor: 'blue' }}><Text>Box2</Text></View>
      <View style={{ flex: 3, backgroundColor: 'gray' }}><Text>Box3</Text></View>
    </View>
```

就表示 `flex` 總數會等於 6，所以第一個 `View` 會佔滿 1/6 個版面，而第二個 `View` 會佔滿 2/6，第三個 `View` 會佔滿 3/6：：

<img src="/images/ReactNative/9_4.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

`flex` 除了切割版面之外，如果再加入 `flexDirection` 則可以設定要垂直切割或者水平切割：

```js
import { StyleSheet, View, Text } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <View style={{ flex: 1, backgroundColor: 'red' }}><Text>Box1</Text></View>
      <View style={{ flex: 1, backgroundColor: 'blue' }}><Text>Box2</Text></View>
      <View style={{ flex: 1, backgroundColor: 'gray' }}><Text>Box3</Text></View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    margin: 24,
    flexDirection: 'row'
  }
});
```

如果沒有特別宣告 `flexDirection` 的話，就會是垂直切割，設定為 `row`，則會變成水平切割：

<img src="/images/ReactNative/9_5.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

[本單元完整程式碼範例](https://snack.expo.dev/@mrjk/day9---flex)

<div data-snack-id="@mrjk/day9---flex" data-snack-platform="web" data-snack-preview="true" data-snack-theme="dark" style="overflow:hidden;background:#0C0D0E;border:1px solid var(--color-border);border-radius:4px;height:505px;width:100%"></div>
<script async src="https://snack.expo.dev/embed.js"></script>

**ReactNative 從零開始學¹ - Day9 [完]**

- 上一篇：[ReactNative 從零開始學¹ - Day8 - ActivityIndicator](/ReactNative/Day8)
- 下一篇：