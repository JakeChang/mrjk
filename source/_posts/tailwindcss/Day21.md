---
title: tailwindcss 從零開始學¹ - Day21 - table 行列固定
date: 2023-09-28 12:38:39
tags:
---
在上一個單元了解到如何建立一個基本款的表格樣式，在表格的顯示方式，如果表格的行或列的數目太多，會希望在滑動的時候卡住某一行或某一列定住在原位置不動，就像使用 Google Sheet 那樣。

例如，這個表格會希望在往左滑動時，原本的第一行會卡住在原本位置不動：

![https://ithelp.ithome.com.tw/upload/images/20230928/20162607gE4NsZX8ZC.png](https://ithelp.ithome.com.tw/upload/images/20230928/20162607gE4NsZX8ZC.png)

向上滑動也是以此類推，這個單元先討論左右滑動的方式，首先延續上一個單元的表格樣式：

```html
<div class="h-full overflow-x-scroll">
  <table class="min-w-full">
    <thead class="border-b bg-white">
      <tr>
        <th class="py-2 pl-8 text-left text-xs font-medium text-gray-500">#1</th>
      </tr>
    </thead>
    <tbody class="divide-y divide-gray-200 bg-white">
      <tr class="border-b bg-neutral-100">
        <td class="py-2 pl-8 text-sm font-light text-gray-500">11111</td>
      </tr>
    </tbody>
  </table>
</div>
```

但因為行數不夠，增加到 20 行：

```html
<div class="h-full overflow-x-scroll">
  <table class="min-w-full">
    <thead class="border-b bg-white">
      <tr>
        <th class="py-2 pl-8 text-left text-xs font-medium text-gray-500">#1</th>
        <th class="py-2 pl-8 text-left text-xs font-medium text-gray-500">#2</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#3</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#4</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#5</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#6</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#7</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#8</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#9</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#10</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#11</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#12</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#13</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#14</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#15</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#16</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#17</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#18</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#19</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#20</th>
      </tr>
    </thead>
    <tbody class="divide-y divide-gray-200 bg-white">
      <tr class="border-b bg-neutral-100">
        <td class="py-2 pl-8 text-sm font-light text-gray-500">11111</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">22222</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">33333</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">44444</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">55555</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">66666</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">77777</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">88888</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">99999</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">00000</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">11111</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">22222</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">33333</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">44444</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">55555</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">66666</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">77777</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">88888</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">99999</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">00000</td>
      </tr>
    </tbody>
  </table>
</div>
```

關鍵的技巧要使用固定某一行，需要使用 `sticky` 可以固定住，還必須要指定固定的位置 `left-0`，所以 `sticky` 與 `left-0` 就表示會固定在左邊位置為 0 的地方。

所以加入到某一個 th 與 td：

```html
<th class="py-2 pl-8 text-left text-xs font-medium text-gray-500 sticky left-0">#1</th>
```

```html
<td class="py-2 pl-8 text-sm font-light text-gray-500 sticky left-0">11111</td>
```

但這樣的效果在滑動時，會發現產生了重疊畫面的問題：

![https://ithelp.ithome.com.tw/upload/images/20230928/201626075MizsG42SD.png](https://ithelp.ithome.com.tw/upload/images/20230928/201626075MizsG42SD.png)

要解決這個問題最簡單的方式就是使用加入背景顏色，就可以輕鬆處理掉，所以最後的完整樣式為：

```html
<div class="h-full overflow-x-scroll">
  <table class="min-w-full">
    <thead class="sticky top-0 border-b bg-white">
      <tr>
        <th class="py-2 pl-8 text-left text-xs font-medium text-gray-500 sticky left-0 bg-white">#1</th>
        <th class="py-2 pl-8 text-left text-xs font-medium text-gray-500">#2</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#3</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#4</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#5</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#6</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#7</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#8</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#9</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#10</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#11</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#12</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#13</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#14</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#15</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#16</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#17</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#18</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#19</th>
        <th class="px-6 py-2 text-left text-xs font-medium text-gray-500">#20</th>
      </tr>
    </thead>
    <tbody class="divide-y divide-gray-200 bg-white">
      <tr class="border-b bg-neutral-100">
        <td class="py-2 pl-8 text-sm font-light text-gray-500 sticky left-0 bg-neutral-100">11111</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">22222</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">33333</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">44444</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">55555</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">66666</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">77777</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">88888</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">99999</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">00000</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">11111</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">22222</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">33333</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">44444</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">55555</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">66666</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">77777</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">88888</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">99999</td>
        <td class="py-2 pl-8 text-sm font-light text-gray-500">00000</td>
      </tr>
    </tbody>
  </table>
</div>
```

最後如果要針對列數的固定，可以使用 `top-16` 讓 td 固定在距離上方位置 16 的地方。

[今日完整範例](https://play.tailwindcss.com/x68FxdKBHC)

**tailwindcss 從零開始學¹ - Day21 [完]**