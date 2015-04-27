---
layout: post
title: Fresco - an image management library
date: 2015-04-25 15:27:31
---

![fresco](http://facebook.github.io/fresco/static/fresco-og-image.png)

臉書在F8發表了自己的Image Loader Library(Android)叫做[Fresco](http://frescolib.org/)，因為他們在市面上找不到完全符合需求的Library，所以自己就寫了一個(這邏輯很Facebook)，它主要強調功能有五：

- 有更佳的記憶體管理
- 支援Progressive JPEG
- Animation Format(GIF和WebP)
- Drawing(更整合customize layer：例如想要塞浮水印之類的)
- 更加的Loading體驗。

針對第五點想要特別強調：

- 它可以同時設定多種resolution的圖片，讓較低解析度的圖片先秀出
- 支援EXIF Thumbnail
- Auto-resize rotation(base on EXIF)
- 讓Android 2.3的裝置也支援WebP。

翻了翻它的source code發現，所以decoder都適用NDK寫的，包含jpeg、png、gif跟WebP真的是佛心來著。看來該把原本在用的[Ion](https://github.com/koush/ion)拔掉了。
