---
title: Hexo 6.0修改样式
date: 2023-01-07 14:50:00

categories:
  - [博客]

tags:
  - Hexo
  - 博客

reward: true
comment: true
---

> 2023 年重新抓回写博客的好习惯，发现 `hexo 6.0` 好像没有暴露出修改的文件

<!-- more -->

---

我想使用代码块\`\`来高亮某句文案，但是发现，默认样式实在是太丑了，想着更以前一样修改样式，找了一圈实在没找到样式文件。

修改其实很简单，只需要在`根文件夹` > `source` 创建 `_data` 文件夹，再创建 `styles.styl` 文件即可。

例如我当前的代码块样式

```css
code{
    background: #d1939e;
    color #fff;
}
```
