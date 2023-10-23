---
title: ReactNative 從零開始學¹ - Day6 - Modal
date: 2023-10-23 12:32:55
tags:
---

這個單元要來討論 Modal 的做法，Modal 表示可以新開一個視窗，在手機上可以表示開啟第二頁。

首先，新增一個按鈕：

```js
import { useState } from 'react';
import { Button, StyleSheet, View, Text } from 'react-native';

export default function App() {
  const buttonTapped = () => {
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

這個按鈕的做法在之前的單元有介紹過。這邊放入一個按鈕，希望可以在按下這個按鈕之後使用 Modal 進而跳轉到第二頁。

接下來直接新增一個 Modal：

```js
import { useState } from 'react';
import { Button, StyleSheet, View, Text, Modal } from 'react-native';

export default function App() {
  const buttonTapped = () => {
  };

  return (
    <View style={styles.container}>
      <Button title="button" color='red' onPress={buttonTapped} />

      <Modal>
        <View style={styles.modal}>
          <Text>Hello Page2</Text>
        </View>
      </Modal>
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
  modal: {
    flex: 1,
    backgroundColor: 'gray',
    alignItems: 'center',
    justifyContent: 'center',
    padding: 24,
  },
});
```

使用 Modal 之前，要先引用 Modal，所以在 import 內新增 Modal。

可以把 Modal 視為新的一頁，所以子層內需要先放入 `<View></View>`，然後才可以放入 UI 元件，這邊我先放上文字 `<Text>Hello Page2</Text>`。

而在這個 Modal 內的 View，另外宣告了一個新的樣式 modal。

但這個時候用模擬器顯示時，會發現整個頁面都被 Modal 所蓋住了：

<img src="/images/ReactNative/6_1.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

所以這個時候必須要先讓 Modal 隱藏起來，然後按下按鈕時才要顯示出來，需要另外宣告一個變數來表示 Modal 是否隱藏：

```js
const [isModalShow, setIsModalShow] = useState(false);
```

宣告一個變數 isModalShow ，型別使用布林，初始值為 false。

接下來就可以在 Modal 來指定到這個變數 isModalShow：

```js
<Modal visible={isModalShow}>
  <View style={styles.modal}>
    <Text>Hello Page2</Text>
  </View>
</Modal>
```

在 Modal 內使用屬性 visible 指定到這個變數，接下來在按鈕函式內設定 isModalShow 變數：

```js
const buttonTapped = () => {
  setIsModalShow(true);
};
```

完整程式碼：

```js
export default function App() {
  const [isModalShow, setIsModalShow] = useState(false);

  const buttonTapped = () => {
    setIsModalShow(true);
  };

  return (
    <View style={styles.container}>
      <Button title="button" color='red' onPress={buttonTapped} />

      <Modal visible={isModalShow}>
        <View style={styles.modal}>
          <Text>Hello Page2</Text>
        </View>
      </Modal>
    </View>
  );
}
```

所以按鈕按下時，這個 Modal 就會被顯示出來了。

但顯示 Modal 時，並沒有辦法回到上一頁，可以新增一個按鈕來解決：

```js
<Modal visible={isModalShow} animationType='fade' presentationStyle='pageSheet'>
  <View style={styles.modal}>
    <Text>Hello Page2</Text>
    <Button title="back" color='blue' onPress={() => setIsModalShow(false)} />
  </View>
</Modal>
```

直接新增一個 `<Button>` 並且在 onPress 屬性內直接將 isModalShow 設定為 false，就可以使 Modal 不顯示，也就是可以直接回到初始頁面的狀態。

而在 Modal 也可以設定動畫屬性：

```js
<Modal visible={isModalShow} animationType='fade'>
  <View style={styles.modal}>
    <Text>Hello Page2</Text>
    <Button title="back" color='blue' onPress={() => setIsModalShow(false)} />
  </View>
</Modal>
```

屬性 `animationType` 有兩種可以設定 `fade` 或者 `slide`。

而在 Modal 也可以設定頁面屬性：

```js
<Modal visible={isModalShow} animationType='fade' presentationStyle='pageSheet'>
  <View style={styles.modal}>
    <Text>Hello Page2</Text>
    <Button title="back" color='blue' onPress={() => setIsModalShow(false)} />
  </View>
</Modal>
```

屬性 `presentationStyle` 設定 `pageSheet`，在 iOS 模擬器上就會顯示成：

<img src="/images/ReactNative/6_2.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

[本單元完整程式碼範例](https://snack.expo.dev/@mrjk/day6---modal)

<div data-snack-id="@mrjk/day6---modal" data-snack-platform="ios" data-snack-preview="true" data-snack-theme="dark" style="overflow:hidden;background:#0C0D0E;border:1px solid var(--color-border);border-radius:4px;height:505px;width:100%"></div>
<script async src="https://snack.expo.dev/embed.js"></script>

**ReactNative 從零開始學¹ - Day6 [完]**

- 上一篇：[ReactNative 從零開始學¹ - Day5 - ScrollView](/ReactNative/Day5)
- 下一篇：
