---
title: ReactNative 從零開始學¹ - Day5 - ScrollView
date: 2023-10-19 12:23:17
tags: ReactNative
---

如果在 Text 內有超過螢幕高度的內容時，要如何讓畫面可以滑動？

先宣告 Text：

```js
import { ScrollView, StyleSheet, Text, View } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
        <Text>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent scelerisque nec nibh sed mollis. Aenean finibus augue diam, at vulputate odio maximus vitae. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Vestibulum ultrices mollis ex finibus dignissim. Integer at varius ex, eget egestas nisi. Nunc imperdiet mi ligula, eget fringilla erat varius a. Nunc quis nibh venenatis, vestibulum elit vitae, pulvinar purus.

          Praesent mollis, justo in blandit interdum, elit lorem cursus tortor, sit amet ultrices nulla mauris quis libero. Integer quis mi risus. Aenean nunc quam, pretium non dictum ut, pharetra vitae nulla. Vivamus rutrum lacus eget mattis tincidunt. Nulla tincidunt sapien velit, vitae ultricies est condimentum ac. Donec ipsum nisi, pulvinar sed odio sit amet, finibus mollis orci. Integer non feugiat dolor. Aliquam tortor urna, gravida eget libero tincidunt, aliquam vulputate neque. Fusce molestie, justo sed malesuada consectetur, lectus elit mollis ligula, in elementum nisl tortor in quam. Proin pharetra arcu ut ante tincidunt efficitur. Nam dictum libero dignissim ligula faucibus, sit amet mollis tellus vehicula. Nam convallis cursus felis eu luctus. Aliquam egestas nunc tellus, id imperdiet metus volutpat eget. Vestibulum vulputate, leo nec porttitor sagittis, dui justo molestie nisi, vel faucibus elit urna id nibh. Suspendisse accumsan pharetra magna consequat dignissim.

          Pellentesque felis odio, rutrum id nibh ut, lacinia tempus risus. Donec ac purus maximus sem tincidunt accumsan id vel elit. Donec nec porttitor arcu. Nam eget urna quis ligula vehicula tristique non sed justo. Suspendisse potenti. Etiam vestibulum ligula et vulputate egestas. Maecenas iaculis id dui vel interdum. Aenean a dapibus diam. Vestibulum et volutpat risus, nec sollicitudin metus.

          Vestibulum id risus non ex elementum porttitor. Aliquam feugiat, mauris sit amet viverra porttitor, velit eros euismod orci, non semper turpis nulla quis nibh. Pellentesque augue purus, iaculis quis dolor id, rhoncus eleifend turpis. Vestibulum ac pulvinar ex, vel finibus justo. Curabitur eget ultricies dolor. Maecenas eget ipsum rutrum, egestas risus id, sodales dolor. Ut tincidunt ex ut nunc mollis, vestibulum scelerisque lectus porttitor. Sed laoreet dapibus nulla vitae vulputate. Vivamus magna orci, posuere at sem id, tempus dapibus magna.

          Vestibulum dolor turpis, pharetra id pharetra vitae, maximus et dui. Proin elementum aliquet mauris at molestie. Integer eu metus vitae lectus sodales venenatis in sit amet elit. Donec eu tortor et massa vestibulum convallis non vel erat. Pellentesque et ornare mi. Maecenas purus nisi, sollicitudin sit amet sem eget, hendrerit laoreet sapien. Donec vitae luctus erat. Integer dignissim tristique eros ac elementum.
        </Text>
    </View>
  );
}
```

這裡放入了非常大量的文字內容，要讓滑面可以滑動，需要加入 `<ScrollView>`：

```js
<ScrollView>
    <Text>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent scelerisque nec nibh sed mollis. Aenean finibus augue diam, at vulputate odio maximus vitae. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Vestibulum ultrices mollis ex finibus dignissim. Integer at varius ex, eget egestas nisi. Nunc imperdiet mi ligula, eget fringilla erat varius a. Nunc quis nibh venenatis, vestibulum elit vitae, pulvinar purus.

        Praesent mollis, justo in blandit interdum, elit lorem cursus tortor, sit amet ultrices nulla mauris quis libero. Integer quis mi risus. Aenean nunc quam, pretium non dictum ut, pharetra vitae nulla. Vivamus rutrum lacus eget mattis tincidunt. Nulla tincidunt sapien velit, vitae ultricies est condimentum ac. Donec ipsum nisi, pulvinar sed odio sit amet, finibus mollis orci. Integer non feugiat dolor. Aliquam tortor urna, gravida eget libero tincidunt, aliquam vulputate neque. Fusce molestie, justo sed malesuada consectetur, lectus elit mollis ligula, in elementum nisl tortor in quam. Proin pharetra arcu ut ante tincidunt efficitur. Nam dictum libero dignissim ligula faucibus, sit amet mollis tellus vehicula. Nam convallis cursus felis eu luctus. Aliquam egestas nunc tellus, id imperdiet metus volutpat eget. Vestibulum vulputate, leo nec porttitor sagittis, dui justo molestie nisi, vel faucibus elit urna id nibh. Suspendisse accumsan pharetra magna consequat dignissim.

        Pellentesque felis odio, rutrum id nibh ut, lacinia tempus risus. Donec ac purus maximus sem tincidunt accumsan id vel elit. Donec nec porttitor arcu. Nam eget urna quis ligula vehicula tristique non sed justo. Suspendisse potenti. Etiam vestibulum ligula et vulputate egestas. Maecenas iaculis id dui vel interdum. Aenean a dapibus diam. Vestibulum et volutpat risus, nec sollicitudin metus.

        Vestibulum id risus non ex elementum porttitor. Aliquam feugiat, mauris sit amet viverra porttitor, velit eros euismod orci, non semper turpis nulla quis nibh. Pellentesque augue purus, iaculis quis dolor id, rhoncus eleifend turpis. Vestibulum ac pulvinar ex, vel finibus justo. Curabitur eget ultricies dolor. Maecenas eget ipsum rutrum, egestas risus id, sodales dolor. Ut tincidunt ex ut nunc mollis, vestibulum scelerisque lectus porttitor. Sed laoreet dapibus nulla vitae vulputate. Vivamus magna orci, posuere at sem id, tempus dapibus magna.

        Vestibulum dolor turpis, pharetra id pharetra vitae, maximus et dui. Proin elementum aliquet mauris at molestie. Integer eu metus vitae lectus sodales venenatis in sit amet elit. Donec eu tortor et massa vestibulum convallis non vel erat. Pellentesque et ornare mi. Maecenas purus nisi, sollicitudin sit amet sem eget, hendrerit laoreet sapien. Donec vitae luctus erat. Integer dignissim tristique eros ac elementum.
    </Text>
</ScrollView>
```

如此就可以讓畫面產生滑動的效果，呈現如：

<img src="/images/ReactNative/5_1.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

[本單元完整程式碼範例](https://snack.expo.dev/@mrjk/day5---scrollview)

<div data-snack-id="@mrjk/day4" data-snack-platform="web" data-snack-preview="true" data-snack-theme="dark" style="overflow:hidden;background:#0C0D0E;border:1px solid var(--color-border);border-radius:4px;height:505px;width:100%"></div>
<script async src="https://snack.expo.dev/embed.js"></script>

**ReactNative 從零開始學¹ - Day5 [完]**

- 上一篇：[ReactNative 從零開始學¹ - Day4 - Button](/ReactNative/Day4)
- 下一篇：[ReactNative 從零開始學¹ - Day6 - Modal](/ReactNative/Day6)
