---
title: ReactNative 從零開始學¹ - Day8 - ActivityIndicator
date: 2023-10-25 12:23:41
tags: ReactNative
---

這個單元要來討論讀取元件的做法，讀取元件稱為 `ActivityIndicator`。

首先先引入 `ActivityIndicator` 這個元件，直接放入 `ActivityIndicator` 元件：

```js
import { StyleSheet, View, ActivityIndicator } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <ActivityIndicator />
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

模擬器顯示：

<img src="/images/ReactNative/8_1.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

將 ActivityIndicator 放大，設定屬性 `size` 為 `large`：

```js
<ActivityIndicator size={'large'} />
```

模擬器顯示：

<img src="/images/ReactNative/8_2.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

將 ActivityIndicator 改變顏色，設定屬性 `color`，這裡使用紅色為範例：

```js
<ActivityIndicator size={'large'} color={'red'} />
```

模擬器顯示：

<img src="/images/ReactNative/8_3.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

設定是否顯示動畫，設定屬性 `animating` 為 `false`：

```js
<ActivityIndicator size={'large'} color={'red'} animating={false}/>
```

在模擬器上面會直接隱藏。

[本單元完整程式碼範例](https://snack.expo.dev/@mrjk/day8---activityindicator)

<div data-snack-id="@mrjk/day8---activityindicator" data-snack-platform="web" data-snack-preview="true" data-snack-theme="dark" style="overflow:hidden;background:#0C0D0E;border:1px solid var(--color-border);border-radius:4px;height:505px;width:100%"></div>
<script async src="https://snack.expo.dev/embed.js"></script>

**ReactNative 從零開始學¹ - Day8 [完]**

- 上一篇：[ReactNative 從零開始學¹ - Day7 - Alert](/ReactNative/Day7)
- 下一篇：[ReactNative 從零開始學¹ - Day9 - Style Flex](/ReactNative/Day9)