---
title: 使用uni-app遇见的坑-2
date: 2019-09-17 11:35:48

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

> 在使用类名为 `header` 时样式不能读取

<!-- more -->

## 问题

在某次项目中，定义了某个元素 `class` 为 `header` 发现样式根本不起作用

## 解决方法（仅供参考）

找了找资料发现这里确实存在着一些小坑，在[uniapp 官网](https://uniapp.dcloud.io/use?id=%e5%91%bd%e5%90%8d%e9%99%90%e5%88%b6)有记载，**命名方式存在限制**。

在 uni-app 中以下这些作为保留关键字，不可作为组件名。
`a, canvas, cell, content, countdown, datepicker, div, element, embed, header, image, img, indicator, input, link, list, loading-indicator, loading, marquee, meta, refresh, richtext, script, scrollable, scroller, select, slider-neighbor, slider, slot, span, spinner, style, svg, switch, tabbar, tabheader, template, text, textarea, timepicker, trisition-group, trisition, video, view, web, Tips`

_除以上列表中的名称外，标准的 HTML 及 SVG 标签名也不能作为组件名。_

---

> 如果文中有什么不足或者不准确的地方，请各位大佬提出来，一起进步，谢谢！
