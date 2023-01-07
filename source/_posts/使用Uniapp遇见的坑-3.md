---
title: 使用uni-app遇见的坑-3
date: 2019-09-19 14:44:02

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

> 在使用方法 `uni.getStorageSync` 在 **_H5_** 页面报
> `SyntaxError: Unexpected token Z in JSON at position 1` 的错误

<!-- more -->

## 问题

_如上所说_

## 解决方法（仅供参考）

自己研究了一下代码，发现 `uni.getStorageSync` 在 **_本地存储_** 为 **null** 或者 **单个字符串** 的时候会出现这个错误，以为这个方法读取的是一个 `Object` 的格式，所以会出现这个问题。

我的解决方式是一开始先判定 **本地存储** 里有无所需的字段，如果为 `null` 、`underfind` 、`空值` 的时候使用 `uni.setStorage` 创建一个记录，再来使用。

`需要注意的是定义的字段名最好不要设置为大众化的，以防相同产生Bug`

---

> 如果文中有什么不足或者不准确的地方，请各位大佬提出来，一起进步，谢谢！
