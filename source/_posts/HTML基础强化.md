---
title: HTML基础强化
date: 2019-07-16 16:35:33
tags:
 - 系统梳理CSS工作应用
 - css

photos:
 - https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/css-1.jpg
---

HTML常见元素、版本（HTML4/XHTML/HTML5的关系）以及HTML元素的分类和嵌套关系。关注元素默认样式和定制化。

<!-- more -->

### <font color=#4fc08d>\#</font>HTML常见元素和理解

声明页面编码格式 :
```html
<!-- html4写法 -->
<meta heep-equiv="Content-Type" content="text/html; charset=utf-8">
<!-- html5写法 -->
<meta charset="UTF-8">
```
<br/>

视口(viewport) :
* width=device-width  视口宽度为设备宽度
* initial-scale=1.0   初始化缩放比例为1 
* maximum-scale=1.0     最大缩放比例为1
* user-scalable=no      不允许用户自由缩放

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, 
maximum-scale=1.0, user-scalable=no">
```

<br/>

声明IE浏览器解析网页时使用的文档模式 :
```html
<meta http-equiv="X-UA-Compatible" content="ie=edge">
```

<br/>

指定基础路径，页面所有链接都会加入基础路径 :
```html
<base href="/">
```

<br/>

HTML语义化
>HTML文档语义化检查工具 http://h5o.github.io

<br/>

### <font color=#4fc08d>\#</font>HTML版本

>HTML结构是否正确验证工具 https://validator.w3.org

* HTML4/4.01基于(SGML),SGML为XML的超集
* XHTML基于(XML)--最严格
* HTML5

| HTML4         | XHTML           | HTML5  |
| :-------------: |:-------------:| :-----:|
| 标签允许不结束  | 标签必须结束    | 标签允许不结束 |
| 属性不用带引号  | 属性必须带引号   |   属性不用带引号 |
| 标签属性可大写  | 标签属性必须小写      |    标签属性可大写 |
| Boolean属性可省略 | Boolean属性不可省略     |    Boolean属性可省略 |

```html
<body>
  <div class="test">合法</div>
  <DIV class="test">标签名大写</DIV>
  <div ID="test">属性名大写</div>
  <p>标签不结束
  <div style=color:red>属性不加引号</div>
</body>
```

<br/>

HTML5新增区块标签
* section
* article
* nav
* aside


HTML5新增表单增强
* 日期、时间、搜索
* 表单验证
* placeholder


HTML5新增语义
* header/footer 头尾
* section/article 区域
* nav 导航
* aside 不重要内容
* em/strong 强调
* i icon 表示图标

<br/>

### <font color=#4fc08d>\#</font>HTML元素分类

按默认样式分
* 块级 block
* 行内 inline
* inline-block

```html
<div>块级元素</div>
<p><span>行内元素</span><em>行内元素</em></p>
<p><select><option>下拉框</option></select><span>select为行内块元素</span></p>
```
<br/>

按内容分
>元素分布图 https://html.spec.whatwg.org/multipage/dom.html#phrasing-content

{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/html_fb.png %} 

* flow 文档流中的元素
* interactive 于用户有交互的元素 a, button
* embedded 嵌入外部资源元素 video
* heading h1-h6
* metadata 头部meta元素
* phrasing 短语元素 em、strong
* sectioning 区域块级元素 section

<br/>

### <font color=#4fc08d>\#</font>HTML元素嵌套关系
适用html4，部分适用html5
* 块级元素可以包含行内元素
* 块级元素不一定能包含块级元素
* 行内元素一般不能包含块级元素
  * a元素可以包含块级元素
    注:a元素在浏览器计算内容模型的时候时不参与计算的，所以在渲染时a不存在

```html
<body>
  <div><a>DIV &gt; A</a></div>
  <!-- 计算内容模型时a标签不参与计算，所以相当于body包含div标签 -->
  <a><div>A &gt; DIV</div></a>
  <!-- a标签不参与计算,所以是p包含div，不合法 -->
  <p><a><div>P &gt; A &gt; DIV</div></a></p>
</body>
```

<br/>

### <font color=#4fc08d>\#</font>默认样式和RESET
>css重置样式库https://necolas.github.io/normalize.css/

保留所有元素的margin、padding等默认样式，尽可能的将所有浏览器默认样式重置为相同样式
