---
title: 使用uni-app遇见的坑-1
date: 2019-08-29 15:22:22

tags: 
- webApp
- uni-app

categories: 
- [前端]

reward: true
comment: true
---

在使用 uni-app 开发 webApp 的时候，总会遇见或多或小的坑

> 如果一个元素根据body定位，在手机端会出现定位不准的问题

<!-- more -->

## 问题
某个元素使用 *position: absolute* 的时候，如果父级是page或者类似的元素，在手机端会出现定位不准确的问题



## 解决方法（仅供参考）
**使用Uniapp特有的一个判断来实现**

可使用* #ifdef APP-PLUS * 来判定当前页面是否为手机端

示例
~~~ bash
	/* #ifdef APP-PLUS */
	top: calc(【你的原始变量】 + var(--status-bar-height));
	/* #endif */
~~~

---

> 如果文中有什么不足或者不准确的地方，请各位大佬提出来，一起进步，谢谢！
<!-- ![测试图片](http://zh.mweb.im/asset/img/set-up-git.gif) -->