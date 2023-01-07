---
title: 使用uni-app遇见的坑-5
date: 2019-11-27 16:34:27

tags:
  - 前端
  - 多端开发
  - uni-app

categories:
  - [uni-app]

reward: true
comment: true
---

在使用 uni-app 开发 webApp 的时候，总会遇见或多或小的坑

> 在使用 uni-app 开发网站时，会出现图片 '闪一下' 的白色闪动效果。

<!-- more -->

## 问题

_如上所说_

（我是设置了 image 为 `mode="widthFix"`），官方解释是 **页面结构复杂，css 样式太多的情况，使用 image 可能导致样式生效较慢** （我测试的时候图片 10KB 左右）

## 解决方法（仅供参考）

官方也针对这个问题进行了修复：设置 `image{will-change: transform}` 可优化此问题。
[链接在此](https://uniapp.dcloud.io/component/image?id=image)

可是我发现这个设置不太能解决我所遇到的问题。

于是自己摸索了一下，发现每次进入的时候图片会有个固定的高度，再依据 `mode` 的属性来更改图片的配置。
这就好办了，我在 APP.vue 里面设置全局 `image` 属性为 `height: 0`， 发现这个问题就这样被解决了。

> 我不知道以后会不会衍生出奇怪的问题出来，但程序世界里不就是这样吗，只有不断探索，才能发现未知呀!

---

> 如果文中有什么不足或者不准确的地方，请各位大佬提出来，一起进步，谢谢！
