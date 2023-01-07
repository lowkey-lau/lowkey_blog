---
title: 记录个人使用SCSS的小知识
date: 2019-12-06 18:19:09

tags:
  - [css, scss]

categories:
  - [前端]
---

> 我个人使用的是 Scss/Sass 的 css 编码手法，在工作上会经常遇到比较有价值的小知识，在这里记录。

<!-- more -->

---

### 对 `scss` 变量做 `calc` 计算的方法

> 在使用 scss 编译的时候，直接使用 **calc($x + $y)** ，浏览器是不能识别的。于是找了一下相关的资料，发现需要使用 **#{$x}** 才可以使用

```scss
// 范例
$x: 20px;
width: calc(#{$x} + 100%);

> width: calc(20px + 100%);
```

---

#END
