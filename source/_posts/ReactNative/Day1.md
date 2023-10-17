---
title: ReactNative 從零開始學¹ - Day1 - 建立專案
date: 2023-10-12 12:19:00
tags: ReactNative
---

### 建立專案

在終端機執行指令：

```bash
npx create-expo-app ReactNative-demo
```

進入到專案資料夾內來啟動專案：

```bash
cd ReactNative-demo
npx expo start
```

啟動成功後，會出現以下訊息：

```bash
Starting project at /Users/jake/Desktop/ReactNative-demo
Starting Metro Bundler
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
█ ▄▄▄▄▄ █▄▄▄ ▀ ▀█▄█ ▄▄▄▄▄ █
█ █   █ ██▄▀ █ ▀█▄█ █   █ █
█ █▄▄▄█ ██▀▄ ▄▄██▀█ █▄▄▄█ █
█▄▄▄▄▄▄▄█ ▀▄█ ▀▄▀ █▄▄▄▄▄▄▄█
█ ▄▀  █▄▀▀▄▀█▄▀█▀ █▄█▀█▀▀▄█
█▀█▄█▀▀▄ ▄▄██▄▄▄▄▀▀███▄▀▀ █
█▀██  ▀▄▀ ▄ █▀█▄ █ ▄▀▀█▀ ██
█ ▄  ▄ ▄▄▀█▄█▀▄▀ ▄▀ ██▄▀  █
█▄█▄▄█▄▄▄ █  ▄▄ █ ▄▄▄  ▄▀▄█
█ ▄▄▄▄▄ ██▄▀▀▄  █ █▄█ ███ █
█ █   █ █ ▄▄▄ ▀█▄ ▄  ▄ █▀▀█
█ █▄▄▄█ █▀▀▀ ▀█▄ ▄█▀▀▄█   █
█▄▄▄▄▄▄▄█▄▄▄▄██▄▄▄▄█▄▄███▄█

› Metro waiting on exp://192.168.0.209:8081
› Scan the QR code above with Expo Go (Android) or the Camera app (iOS)

› Using Expo Go
› Press s │ switch to development build

› Press a │ open Android
› Press i │ open iOS simulator
› Press w │ open web

› Press j │ open debugger
› Press r │ reload app
› Press m │ toggle menu
› Press o │ open project code in your editor

› Press ? │ show all commands

Logs for your project will appear below. Press Ctrl+C to exit.
```

### iOS App

接下來按下鍵盤 i 鍵，會自動開啟 iPhone 模擬器：

```bash
› Opening on iOS...
› Opening exp://192.168.0.209:8081 on iPhone SE (3rd generation)
Downloading the Expo Go app [================================================================] 100% 0.0s


› Press ? │ show all commands
› Opening the iOS simulator, this might take a moment.
iOS Bundling complete 3881ms
```

成功開啟 iPhone 模擬器：

<img src="/images/ReactNative/1_1.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

這個時候回到模擬器的桌面，會發現它會自動安裝 Expo Go 這個 App：

<img src="/images/ReactNative/1_2.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

所以整個 ReactNative 的專案主要是使用 Expo Go 這個 App 來實現。

### Android App

回到終端機按下鍵盤 a 鍵，會自動開啟 Android 模擬器，但這個時候會出現錯誤：

```bash
› Opening on Android...
CommandError: No Android connected device found, and no emulators could be started automatically.
Please connect a device or create an emulator (https://docs.expo.dev/workflow/android-studio-emulator).
Then follow the instructions here to enable USB debugging:
https://developer.android.com/studio/run/device.html#developer-device-options. If you are using Genymotion go to Settings -> ADB, select "Use custom Android SDK tools", and point it at your Android SDK directory.
```

這個時候必須要手動開啟 Android 模擬器，打開 Android Studio 之後，選取 More Actions -> Virtual Device Manager

<img src="/images/ReactNative/1_3.png"  style="display: block;margin-left: auto;margin-right: auto;width: 100%;">

在左上角，按下 Create Device，選取想要使用哪一款手機的模擬器，選好之後，在這頁按下 Play：

<img src="/images/ReactNative/1_4.png"  style="display: block;margin-left: auto;margin-right: auto;width: 100%;">

重新回到終端機按下鍵盤 a 鍵，就可以自動開啟 Android 模擬器：

```bash
› Opening on Android...
› Opening exp://192.168.0.209:8081 on Pixel_3a_API_34_extension_level_7_arm64-v8a
› Press ? │ show all commands
Android Bundling complete 3542ms
```

成功開啟 Android 模擬器：

<img src="/images/ReactNative/1_5.png"  style="display: block;margin-left: auto;margin-right: auto;width: 50%;">

**ReactNative 從零開始學¹ - Day1 [完]**

- 下一篇：[ReactNative 從零開始學¹ - Day2 - Hello World](/ReactNative/Day2)