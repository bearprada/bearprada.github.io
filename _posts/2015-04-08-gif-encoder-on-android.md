---
layout: post
title: GIF Encoder on Android
date: 2015-04-08 15:27:31
---

![GIFCAM for messenger](http://4.bp.blogspot.com/Zd5i6n5rFo1cPPsZO6H87M3JL-WlE2QZ-VRINKSTFaV-f6yCGgZCdkivPF5Hsdm5MF4=w300)

最近跟臉書的Messenger Platform合作了一款新的APP叫做[GIFCAM](http://getgifcam.com/)(希望大家趕快去下載來玩唷！)，看APP的名稱就知道跟GIF格式有所相關，今天想要分享(抱怨)在開發中碰到的痛點之一:GIF Encoder。

為什麼痛呢？第一沒有官方Support的版本(iOS在ImageIO Framework裡)；第二有3rd party library是純JAVA的[Solution](https://github.com/nbadal/android-gif-encoder)，但Performance就是差到很誇張；第三想找NDK但找不到標準或比較常用的Library。

基於上面的思路，想必要自己把它擠出來了，所以我參考了一個半成品叫做[Gifflen](https://github.com/wasabeef/gifflen-sample)，看起來是我們想要的答案，但它Code Style不太像個正常的Library，果然用了之後碰到很多問題，細節之後再透過其他文章跟大家分享，總之為了要達成像iOS ImageIO的效能，我們把GIF的規格認真的看了一遍，一個一個byte去看iOS為什麼可以做得比較好(之後我們會把自己的Gifflen再open source出來)，雖然目前還差iOS很多，但效能跟輸出結果還差強人意，勉強可以通過測試並且上線。

![GIFCAM result](https://piccollage.files.wordpress.com/2015/03/unnamed-1.gif?w=520&h=820)