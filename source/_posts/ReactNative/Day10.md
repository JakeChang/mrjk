---
title: ReactNative 從零開始學¹ - Day10 - justifyContent
date: 2023-10-30 17:09:32
tags: ReactNative
---

這單元繼續討論排版， `flex` 可以幫助設定切割版面的大小，而 `justifyContent` 可以設定垂直方向的位置。

首先一開始先宣告一個 box 的樣式，並且宣告寬度與高度的大小：

```js
import { StyleSheet, View, Text } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <View style={styles.box}><Text>Box1</Text></View>
      <View style={styles.box}><Text>Box2</Text></View>
      <View style={styles.box}><Text>Box3</Text></View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    margin: 44,
  },
  box: {
    width: 50,
    height: 50,
  }
});
```

接下來要分別針對這三個 box 放入不同顏色，使用陣列的方式將 css 樣式帶入：

```js
<View style={styles.container}>
  <View style={[styles.box, { backgroundColor: 'red' }]}><Text>Box1</Text></View>
  <View style={[styles.box, { backgroundColor: 'blue' }]}><Text>Box2</Text></View>
  <View style={[styles.box, { backgroundColor: 'gray' }]}><Text>Box3</Text></View>
</View>
```

開啟模擬器會呈現：

<img src="/images/ReactNative/10_1.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

接下來在上一層的樣式 container 內宣告 `justifyContent`：

```css
container: {
  flex: 1,
  margin: 44,
  justifyContent: 'flex-start'
},
```

`justifyContent` 一共有六種屬性值可以設定：
- flex-start
- flex-end
- center
- space-between
- space-around
- space-evenly

`flex-start` 是表示針對垂直方向的上方對齊，所以設定這個屬性之後，就如同上面的模擬器的樣子一樣。

`flex-end` 是表示針對垂直方向的下方對齊：

```css
justifyContent: 'flex-end'
```

模擬器會呈現：

<img src="/images/ReactNative/10_2.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

`center` 是表示會垂直置中：

```css
justifyContent: 'center'
```

模擬器會呈現：

<img src="/images/ReactNative/10_3.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

`space-between` 是表示會均勻的分佈垂直位置上，並且將剩餘的空間分配到中間相鄰處的地方：

```css
justifyContent: 'space-between'
```
    
模擬器會呈現：

<img src="/images/ReactNative/10_4.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

`space-around` 是表示會均勻的分佈垂直位置上，剩下的空間會先分配到最前面與最後面的空白處：

```css
justifyContent: 'space-around'
```

模擬器會呈現：
    
<img src="/images/ReactNative/10_5.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

`space-evenly` 是表示會均勻的分佈垂直位置上，而且中間相鄰的空間大小會相同，也包含最前面與最後面的空白處：

```css
justifyContent: 'space-evenly'
```

模擬器會呈現：

<img src="/images/ReactNative/10_6.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

**ReactNative 從零開始學¹ - Day10 [完]**

- 上一篇：[ReactNative 從零開始學¹ - Day9 - Style Flex](/ReactNative/Day9)
- 下一篇：