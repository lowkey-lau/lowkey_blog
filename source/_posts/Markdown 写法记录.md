---
title: Markdown 写法记录
date: 2019-09-06 16:58:52

tags: 
- Markdown

categories: 
- [博客]
- [干货]

reward: true
comment: true
---


> 开始记录博客了，可Hexo编写的文章使用Markdown的写法，因此在这里记录一下Markdown的写法

<!-- more -->

---
## Markdown 的创始人

![Aaron Swartz 大神照片](/images/people/Aaron_Swartz.jpg "Aaron Swartz 大神照片")
<!-- > Aaron Swartz 大神照片 -->
---
## 标题
标题共有六个级别,使用 `#` 来区分层级

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```
`注：# 和字符之间建议保留一个字符的空格，这是最标准的 Markdown 写法。`

---

## 语义标记
| 类型 | 效果 | 写法 |
|:------:|:--------:|:-----:|
| 斜体 | *斜体* | `*斜体* _斜体_` |
| 粗体 | **粗体** | `**粗体**` |
| 粗斜体 | ***粗斜体*** | `***粗斜体***` |
| 栅格线 | ~栅格线~ | `~栅格线~` |

---

## 语义标签
| 类型 | 效果 | 写法 |
|:------:|:--------:|:-----:|
| 斜体 | <i>斜体</i> | `<i>斜体</i>` |
| 粗体 | <b>加粗</b> | `<b>加粗</b>` |
| 强调 | <em>强调</em> | `<em>强调</em>` |
| 上标 | Z<sup>a</sup> | `Z<sup>a</sup>` |
| 下标 | Z<sub>a</sub> | `Z<sub>a</sub>` |
| 键盘文本 | <kbd>Ctrl</kbd> | `<kbd>Ctrl</kbd>` |
| 换行 |   | `<br />` |

---

## 代码块
### 单行代码
```
`这是单行代码`
```
显示效果为:
`这是单行代码`

<br/>

### 多行代码
````markdown
```javascript
$(document).ready(function () {
    alert('hello world');
});
```
````

显示效果为:
```javascript
$(document).ready(function () {
    alert('hello world');
});
```

<br/>

### 代码高亮
> 如果你只想高亮语句中的某个函数名或关键字，可以使用 `function_name()` 实现
> 通常编辑器根据代码片段适配合适的高亮方法，但你也可以用 **\`\`\`** 包裹一段代码，并指定一种 **语言**

支持的语言：`1c, abnf, accesslog, actionscript, ada, apache, applescript, arduino, armasm, asciidoc, aspectj, autohotkey, autoit, avrasm, awk, axapta, bash, basic, bnf, brainfuck, cal, capnproto, ceylon, clean, clojure, clojure-repl, cmake, coffeescript, coq, cos, cpp, crmsh, crystal, cs, csp, css, d, dart, delphi, diff, django, dns, dockerfile, dos, dsconfig, dts, dust, ebnf, elixir, elm, erb, erlang, erlang-repl, excel, fix, flix, fortran, fsharp, gams, gauss, gcode, gherkin, glsl, go, golo, gradle, groovy, haml, handlebars, haskell, haxe, hsp, htmlbars, http, hy, inform7, ini, irpf90, java, javascript, json, julia, kotlin, lasso, ldif, leaf, less, lisp, livecodeserver, livescript, llvm, lsl, lua, makefile, markdown, mathematica, matlab, maxima, mel, mercury, mipsasm, mizar, mojolicious, monkey, moonscript, n1ql, nginx, nimrod, nix, nsis, objectivec, ocaml, openscad, oxygene, parser3, perl, pf, php, pony, powershell, processing, profile, prolog, protobuf, puppet, purebasic, python, q, qml, r, rib, roboconf, rsl, ruby, ruleslanguage, rust, scala, scheme, scilab, scss, smali, smalltalk, sml, sqf, sql, stan, stata, step21, stylus, subunit, swift, taggerscript, tap, tcl, tex, thrift, tp, twig, typescript, vala, vbnet, vbscript, vbscript-html, verilog, vhdl, vim, x86asm, xl, xml, xquery, yaml, zephir`

---

## 引用

可以无限制的引用下去

```markdown
> 我是第一级引用
>> 我是第二级引用
>>> 我是第三级引用
>>>> ...
```

显示效果为:
> 我是第一级引用
>> 我是第二级引用
>>> 我是第三级引用
>>>> ...


---

## 列表
### 无序列表
使用 `-` 、 `+` 、 `*` 书写
效果：
- 1
- 2
- 3

### 有序列表
使用 `1.` 、 `2.` 、 `3.` 书写

效果：
1. 1 内容1
2. 2 内容2
7. 7 内容3(会按照序列强制编排,例如我这一行使用的是 `7. ` )

---

##  链接
常用链接方法
```markdown
文字链接 [链接名称](http://链接网址)
网址链接 <http://链接网址>
```

高级链接技巧

```markdown
这个链接用 1 作为网址变量 [Google][1].
这个链接用 yahoo 作为网址变量 [Yahoo!][yahoo].
然后在文档的结尾为变量赋值（网址）
[1]: http://www.google.com/
[yahoo]: http://www.yahoo.com/
```

---



## 图片
> 插入图片不需要其他按钮，你只需要使用 **\!\[](图片链接地址)** 这样的语法即可

```
![我是图片备注](http://zh.mweb.im/asset/img/set-up-git.gif)

另外发现Hexo的Next主题需要: 
 
![我是图片备注](http://zh.mweb.im/asset/img/set-up-git.gif "我是图片备注") 

这种写法才能显示
```

**演示**
![我是图片备注](http://zh.mweb.im/asset/img/set-up-git.gif "我是图片备注")

---


## 图片链接

```
[![我是图片备注](http://zh.mweb.im/asset/img/set-up-git.gif "我是图片备注")](http://www.baidu.com)
```

**演示**
[![我是图片备注](http://zh.mweb.im/asset/img/set-up-git.gif "我是图片备注")](http://www.baidu.com)

---


## 任务列表

```
- [x] 选项一
- [ ] 选项二  
- [ ]  [选项3]
```

**演示**
- [x] 选项一
- [ ] 选项二  
- [ ]  [选项3]

---


## 分割线

分割线的使用方式很简单，使用 `---` 即可生成一条分割线

**演示**

---


## 邮箱链接

```
<xxx@outlook.com>
```

**演示**
<xxx@outlook.com>

## 表格

```
|    a    |       b       |      c     |
|:-------:|:------------- | ----------:|
|   居中  |     左对齐    |   右对齐   |
|   1  |     1    |   1   |
|   2  |     2    |   2   |
```
**演示**

|    a    |       b       |      c     |
|:-------:|:------------- | ----------:|
|   居中  |     左对齐    |   右对齐   |
|   1  |     1    |   1   |
|   2  |     2    |   2   |

>> 我是主题设置了全局左对齐，因此可能没显示 `对齐` 效果，见谅