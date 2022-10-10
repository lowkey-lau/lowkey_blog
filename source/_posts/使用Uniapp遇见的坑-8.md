---
title: 使用uni-app遇见的坑-8
date: 2020-11-16 11:57:27

tags:
- webApp
- uni-app
- subNvue

categories: 
- [前端]

reward: true
comment: true
---

在使用 uni-app 开发 webApp 的时候，总会遇见或多或小的坑

> 在uniapp开发中使用nvue，如果使用了全局样式，就会报一大堆错误，类似这种

![nvue 使用全局样式引起的Bug](/images/subNvue/img-pack-bug.png "nvue使用全局样式引起的Bug") 


<!-- more -->
------

出现这个问题的原因是 `nvue` 使用的编写方式是 `week`，详细的可以看 [Weex](https://weex.apache.org/zh/docs/styles/common-styles.html "Weex")
Emm，看了挺多的别人分享的东西，可是不是很好的呈现效果，然后突然想了想可不可以用平台判断呢，然后查了下官网文档发现有 `#ifndef APP-NVUE` 这个判断，那问题就这么简单的解决了哈哈

![Bug修复](/images/subNvue/img-pack-bug-fixed.png "Bug修复") 



