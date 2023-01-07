---
title: 使用uni-app遇见的坑-7
date: 2020-11-07 15:46:27

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

> 之前遇到一个需求，希望背景是视频的，能自动循环播放且能有声音。这时问题来了，在 uni-app 中视频的层级高于其他前端组件。

## <!-- more -->

关于`视频`这一块，官网也有一个非常详细的描述，看官且看
[uni-app - 视频](https://uniapp.dcloud.io/component/video?id=video "uni-app - 视频")

如果使用正常的布局会发现你编写的组件被视频给覆盖了，这里我使用了两种解决方式：

### 1.使用 cover-view

当你的页面元素不需要很复杂且元素不多的时候，可以使用 `cover-view`
[uni-app - cover-view](https://uniapp.dcloud.io/component/cover-view "uni-app - cover-view")

在 `video` 元素里嵌套使用，不过缺点是只能简单的支持 `cover-view` 和 `cover-image`，事件也仅支持 `@click` 的触发

### 2.使用 subNvue

我是使用这个方法来实现了我的需求，它相当于一个编写一个原生子窗体覆盖在页面上，层级比视频的高
[uni-app - subNvue](https://uniapp.dcloud.io/collocation/frame/subNVues "uni-app - subNvue")

我的使用方法是在视频页同文件夹中添加一个 nvue 的文件，例如：
![](/images/subNvue/img-01.png)
配置完后去 `pages.json` 把 subNvue 文件挂载上去通过 app 预览效果
![](/images/subNvue/img-02.png)

这样就完成了我们想要的效果啦，当然，它是有缺点的，`subNvue` 的写法在 `H5` 是呈现不出效果的，还有 `subNvue` 是使用 `Weex` 的编写手法，样式上有一些局限，具体的各位自行优化把
[Weex](https://weex.apache.org/zh/docs/styles/common-styles.html "Weex")
