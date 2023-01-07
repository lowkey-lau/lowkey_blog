---
title: 使用uni-app遇见的坑-6
date: 2020-11-06 11:00:27

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

> 当主题风格是深色，进行页面切换时会出现白屏闪动的情况，这对用户的体验是不友好的。

<!-- more -->

## 问题

_如上所说_

剖析了 uni-app 的渲染方式，发现他的页面都有个默认的背景颜色生成，这时解决方法就出现了

## 解决方法（仅供参考）

找到 `pages.json` 文件，在主题色的页面结构中添加代码

```
"style": {
	"app-plus": {
		"background": 主题色
	}
}
```

是不是发现这个体验感就好了很多了，当然，如果你全部页面都是同样风格的，可以在 `globalStyle` 中添加全局背景色优化

```
"globalStyle": {
	"app-plus": {
		"background": 主题色
	}

}

```

> 如果文中有什么不足或者不准确的地方，请各位大佬提出来，一起进步，谢谢！
