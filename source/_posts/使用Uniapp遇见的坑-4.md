---
title: 使用uni-app遇见的坑-4
date: 2019-09-27 10:38:27

tags:
- webApp
- uni-app

categories: 
- [前端]

reward: true
comment: true
---

在使用 uni-app 开发 webApp 的时候，总会遇见或多或小的坑

> uni-app中使用父子组件,子组件中的 *onLoad* , *onShow* 方法不执行

<!-- more -->

## 问题

*如上所说*

## 解决方法（仅供参考）
自己研究了一下，发现子组件可以使用 Vue 的 created() 生命周期，或者通过事件通知子组件。

`暂时解决方法就是子组件使用 Vue 的生命周期，可能官方以后出新规则呢~`

---

> 如果文中有什么不足或者不准确的地方，请各位大佬提出来，一起进步，谢谢！
