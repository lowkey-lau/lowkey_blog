---
title: uni-app 遇坑集合
date: 2019-08-29 15:22:22

categories:
  - [uni-app]

tags:
  - 前端
  - 多端开发
  - uni-app

reward: true
comment: true
---

> 前言：在使用 uni-app 开发 webApp 的时候，总会遇见莫名其妙的一些小坑，有些是版本引发的，有一些是小细节引发的。

<!-- more -->

---

## 如果一个元素根据 body 定位，在手机端会出现定位不准的问题

> 元素使用 `position: absolute` 进行定位且 `top: 0` 时，父级是 `page` 情况下，在手机端会出现定位不准确的问题，会被 `状态栏` 所遮盖。

---

**出现这个问题的原因是如果根据 `page` 定位时，最顶部的位置是 `屏幕最顶端` ，会跟 `状态栏` 重叠，造成样式混乱，可以使用官方提供的一个属性 `var(--status-bar-height)` ，来获取状态栏的高度，在定位的时候加上此属性即可。**

[uni-app 官网 - css 变量](https://uniapp.dcloud.net.cn/tutorial/syntax-css.html#css-%E5%8F%98%E9%87%8F)

```bash
	/* #ifdef APP-PLUS */ //判断是否手机端，PC端此属性值为 0
	top: calc(【你的原始变量】 + var(--status-bar-height));
	/* #endif */
```

<br /><br />

## 在使用类名为 `header` 时样式不能读取

> 在开发过程中，定义了某个元素的 `class` 为 `header`， 发现修改的样式不生效。

---

**找了资料发现这里确实有着小坑，在 [uniapp 官网 - 命名限制](https://uniapp.dcloud.net.cn/tutorial/vue-components.html#%E5%91%BD%E5%90%8D%E9%99%90%E5%88%B6) 有记载，`命名方式存在限制`**

**以下特定的字符串会保留关键字，不可作为组件名。**

`a`、`canvas`、`cell`、`content`、`countdown`、`datepicker`、`div`、`element`、`embed`、`header`、`image`、`img`、`indicator`、`input`、`link`、`list`、`loading-indicator`、`loading`、`marquee`、`meta`、`refresh`、`richtext`、`script`、`scrollable`、`scroller`、`select`、`slider-neighbor`、`slider`、`slot`、`span`、`spinner`、`style`、`svg`、`switch`、`tabbar`、`tabheader`、`template`、`text`、`textarea`、`timepicker`、`transition-group`、`transition`、`video`、`view`、`web`

<br /><br />

## 使用方法 `uni.getStorageSync` 在 **_H5_** 页面出现错误

> 在获取本地缓存的数据时，调用 `uni.getStorageSync` 方法，出现错误日志 `SyntaxError: Unexpected token Z in JSON at position 1`

---

**研究了一下代码，发现 `uni.getStorageSync` 在 `本地存储` 为 `null` 或者 `单个字符串` 的时候会出现这个错误，因为这个方法读取的是一个 `Object` 的格式，但它获取不到内容，所以会出现这个 bug。**

**解决方式是方法调用前先判定 `本地存储` 里有无所需的字段，如果为 `null` 、`underfind` 、`空值` 的时使用 `uni.setStorage` 创建一个记录，再来调用它。**

<small>_需要注意的是定义的字段名最好不要设置为大众化的， 例如 language，lang 等，以防相同参数产生 Bug_</small>

<br /><br />

## uni-app 中使用父子组件，子组件中的 `onLoad` , `onShow` 方法不执行

> 在开发过程中，组件开发是最常见的开发模式，但是在 uni-app 中，子组件的生命周期不能使用 `onShow`、 `onLoad`等

---

**看了相关文档，发现组件有它单独的生命周期 [uni-app 官网 - 组件生命周期](https://uniapp.dcloud.net.cn/tutorial/page.html#componentlifecycle)，使用的是 vue 的标准，因此组件开发的生命周期必须区分开来调用。**

<br /><br />

## 在日常开发中，会出现图片 '闪一下' 的白色闪动效果。
