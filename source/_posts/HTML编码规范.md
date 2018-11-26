---
title: HTML编码规范
date: 2016-3-6 13:09:04
tags: [HTML]
---

### 语法
用两个空格来代替tab  这是唯一能保证在所有环境下获得一致展现的方法。
嵌套元素应当缩进一次（即两个空格）。
对于属性的定义，确保全部使用双引号，绝不要使用单引号。
不要在自闭合（self-closing）元素的尾部添加斜线 HTML5 规范中明确说明这是可选的。
不要省略可选的结束标签（closing tag）（例如，&lt;/li&gt; 或 &lt;/body&gt;）。
去除不必要的空格（例如：&lt;/Test&gt;）
``` html
<!DOCTYPE html>
<html>
<head>
    <title>Page title</title>
</head>
<body>
    <img src="images/logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
</body>
</html>
```
<!-- more -->
### HTML5 doctype
为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。
``` html
<!DOCTYPE html>
<html>
  <head>
  </head>
</html>
``` 

### 语言属性
根据 HTML5 规范：强烈建议为 html 根元素指定 lang 属性，从而为文档设置正确的语言。
这将有助于语音合成工具确定其所应该采用的发音，有助于翻译工具确定其翻译时所应遵守的规则等等。(盲人浏览器了解一下...)


``` html
<html lang="zh-CN">
  <!-- ... -->
</html>
``` 
### IE 兼容模式
IE 支持通过特定的 &lt;meta&gt; 标签来确定绘制当前页面所应该采用的 IE 版本。除非有强烈的特殊需求，否则最好是设置为 edge mode，从而通知 IE 采用其所支持的最新的模式。
``` html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
``` 

### 字符编码
通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。这样做的好处是，可以避免在 HTML 中使用字符实体标记（character entity），从而全部与文档编码一致（一般采用 UTF-8 编码）。
``` html
<head>
  <meta charset="UTF-8">
</head>
``` 
### 引入 CSS 和 JavaScript 文件
根据 HTML5 规范，在引入 CSS 和 JavaScript 文件时一般不需要指定 type 属性，因为 text/css 和 text/javascript 分别是它们的默认值。
``` html
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- In-document CSS -->
<style>
  /* ... */
</style>
<!-- JavaScript -->
<script src="code-guide.js"></script>
``` 

### 属性顺序
HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。
class
id, name
data- &#42; 
src, for, type, href
title, alt
aria-&#42;, role
class 用于标识高度可复用组件，因此应该排在首位。id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。


``` html
<a class="..." id="..." data-modal="toggle" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
``` 
### 减少标签的数量
编写 HTML 代码时，尽量避免多余的父元素。请看下面的案例：
``` html
<!-- Bad -->
<span class="avatar">
  <img src="...">
</span>

<!-- Good -->
<img class="avatar" src="...">
``` 


### JavaScript 生成的标签
通过 JavaScript 生成的标签让内容变得不易查找、编辑，并且降低性能。能避免时尽量避免。


版权声明：本文为博主制作文章，转载时注明，谢谢。