---
title: ReactNative 從零開始學¹ - Day2 - Hello World
date: 2023-10-16 12:09:30
tags: ReactNative
---

建立好專案之後，主程式在 App.js：

```js
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text>Open up App.js to start working on your app!</Text>
      <StatusBar style="auto" />
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

前兩行先匯入(import) 必要的元件，這裡要 import 的元件會根據要使用的元件來決定。

然後在第 4 行，宣告一個函式 App，這個函式就是目前 App 的第一頁所顯示的內容。在這裡可以發現所有的 UI 元件都是使用 <> 標籤來包覆起來，如 `<View></View>` 與 `<Text></Text>` 與 `<StatusBar />` 這三個 UI 元件。

而在顯示的樣式則是使用另外一個宣告 `style` 來定義。

例如這邊修改成 Hello World：

```js
export default function App() {
  return (
    <View style={styles.container}>
      <Text>Hello World</Text>
    </View>
  );
}
```

在畫面上就只會顯示一組字串 Hello World。

加入另外一組樣式：

```js
export default function App() {
  return (
    <View style={styles.container}>
      <View style={styles.card}>
        <Text>Hello World</Text>
      </View>
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
  card: {
    backgroundColor: 'red',
    padding: 20,
    color: 'while',
  }
});
```

這邊加入了另外一組樣式 card，並且新增一個 `View` 元件來使用這個 card 樣式，所以在手機上就會呈現：

<img src="/images/ReactNative/2_1.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

但在這裡發現明明已經宣告文字的顏色 `color: 'while'`，但是在呈現上並沒有出現文字為白色的樣式。這是因為在 ReactNative 的樣式定義上各自為獨立使用，且在 `View` 內又包覆了一個 `Text` ，所以這個文字白色的樣式必須要加入在 `Text` 內。

重新宣告一個文字樣式：

```js
export default function App() {
  return (
    <View style={styles.container}>
      <View style={styles.card}>
        <Text style={styles.text}>Hello World</Text>
      </View>
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
  card: {
    backgroundColor: 'red',
    padding: 20,
  },
  text: {
    color: 'white',
  }
});
```

這邊另外宣告一個 text 樣式，並且加入到  `<Text style={styles.text}>`，就可以讓文字變成白色了。

這邊如果在 `Text` 內加入另外一個 `Text`：

```js
export default function App() {
  return (
    <View style={styles.container}>
      <View style={styles.card}>
        <Text style={styles.text}>Hello World
          <Text> JK</Text>
        </Text>
      </View>
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
  card: {
    backgroundColor: 'red',
    padding: 20,
  },
  text: {
    color: 'white',
  }
});
```

在手機上會呈現：

<img src="/images/ReactNative/2_2.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

這邊就可以驗證相同的 UI 元件其所使用的樣式會繼承到子 UI 元件。

[本單元完整程式碼範例](https://snack.expo.dev/@mrjk/day2)

<div data-snack-id="@mrjk/day2" data-snack-platform="ios" data-snack-preview="true" data-snack-theme="dark" style="overflow:hidden;background:#0C0D0E;border:1px solid var(--color-border);border-radius:4px;height:505px;width:100%"></div>
<script async src="https://snack.expo.dev/embed.js"></script>

**ReactNative 從零開始學¹ - Day2 [完]**

- 上一篇：[ReactNative 從零開始學¹ - Day1 - 建立專案](/ReactNative/Day1)
- 下一篇：[ReactNative 從零開始學¹ - Day3 - Button](/ReactNative/Day3)