---
title: "移除旧版本的 Trichrome Library"
slug: "clear-old-trichromelibrary"
date: 2023-03-23T19:56:00+08:00
draft: false
tags: []
categories: []
---

# 原因

智障谷歌会在 Android System Webview 和 Chrome 之间共享一个库，这个库就是 Trichrome Library

但是如果升级 Chrome，新版本的 Trichrome Library 安装后，旧版本的 Trichrome Library 并不会删除，长此以往，存储空间就浪费了

# 删除方法

### 第一步，找到旧版本

**有 root 权限**

直接到 /data/app 下搜索含有 com.google.android.trichromelibrary 的目录

**没有 root 权限**

在连接了 adb 的情况下，执行如下命令获取

```shell
adb shell
dumpsys package | grep name:c
```

### 第二步，删除

无论有没有 root 权限，都应该使用 adb 的 pm 工具进行删除操作

在进行删除时，需要操作的包名并不是 com.google.android.trichromelibrary

而是

```js
const versionCode = '561503734';
const packageName = `com.google.android.trichromelibrary_${versionCode}`;
```

然后执行以下命令卸载即可

```shell
adb shell
pm uninstall com.google.android.trichromelibrary_561503734
```
