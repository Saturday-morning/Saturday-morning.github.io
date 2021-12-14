*本文是对MDN-HTML文档的第一次整理。——苏尔雅*

# 一些东西篇幅较长且属于科普性质的内容
你可以在学习的最后再观看学习：

1. [规划一个简单的网站](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure#%E8%A7%84%E5%88%92%E4%B8%80%E4%B8%AA%E7%AE%80%E5%8D%95%E7%9A%84%E7%BD%91%E7%AB%99)
2. [HTML调试](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/Debugging_HTML)
3. [课后练习1：标记信件](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/Marking_up_a_letter)
4. [课后练习2：构建内容丰富的网页](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/Structuring_a_page_of_content)

# 开始学习 HTML
HTML由一系列的元素组成，它是标记语言。可以把元素**嵌套**到其它元素之中。
![元素与标签](https://mdn.mozillademos.org/files/16475/element.png "元素与标签")

## 块级元素\内联元素\空元素

```html
<!-- html注释 -->
块级元素:
	<title>标题</title>
    <p>段落（paragraph）</p>
	<h1>标题1</h1>
内联元素:
	<em>斜体强调(emphasis)</em>
	<strong>加粗强调</strong>
	<a href="超链接地址" title="鼠标停留显示文字">超链接</a>（如果有属性target="_blank"，将在新标签页中显示链接）
空元素：	
	<img src="图片地址">
	<input type="text" disabled="disabled">（输入框用了布尔属性）
	<input type="text" disabled>（和上面类似，重复的可以省略呵呵）
```

属性的内容要用引号括起来，单双引号可以交替混用。要显示双引号就要实体引用.
块级元素在页面中以块的形式展现，通常用于展示页面上结构化的内容，例如段落、列表、导航菜单、页脚等等。内联元素通常出现在块级元素中，并环绕文档内容的一小部分。
块级元素会出现在单独的一行或几行，它可以嵌套在块级元素中；而内联元素通常关注块级元素里面的一部分内容。
![image](https://mdn.mozillademos.org/files/16476/attribute.png "元素的属性")

## 剖析HTML文档

```html
<!DOCTYPE html>  <!-- 声明文档类型 -->
<html>  <!-- html元素 -->
  <head>  <!-- head元素 -->
    <meta charset="utf-8"><!-- 使用utf-8字符集编码 -->
    <title></title>
  </head>
  <body>
    <p>渲染时，HTML解释器会将连续出现的空白字符减少为一个单独的空格符,我们在HTML元素的嵌套中使用空白就是为了可读性.</p>
  </body>
</html>

| 原义字符 | 等价字符引用 |
    |:----:|--------|
    | <    | &lt;   |
    | >    | &gt;   |
    | "    | &quot; |
    | '    | &apos; |
    | &    | &amp;  |
```

# HTML文件头和它里面的元数据

## 文件头与标签
文件头里的东西是不会在页面里显示出来的。它包含了网页标题、CSS、自定义图标的链接以及其他的元数据，用来给网页贴标签。

```html
<head>
  <meta charset="utf-8"><!-- utf-8字符集全球通用 -->
  <title>网页标题你不会不知道是什么吧？</title>
</head>
```

文件头的标签数据，在爬虫、收藏等方面的信息提取都起到了作用。`meta`	元素中大多包含`name`和`content`属性,`name`指定了元素类型，`content`指定了其内容。合适的标签可以为搜索引擎和其他爬虫更加方便地定位。但是`keyword`标签已经由于滥用被抛弃了。此外，还有一些[其他类型的元数据](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E5%85%B6%E4%BB%96%E7%B1%BB%E5%9E%8B%E7%9A%84%E5%85%83%E6%95%B0%E6%8D%AE)

```html
<meta name="author" content="Chris Mills"><!--就是作者-->
<meta name="description" content="The MDN Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications."><!--描述-->
```

## 图标
页面添加图标的方式有：

1.  将其保存在与网站的索引页面相同的目录中，以.ico格式保存
2.  `<link rel="shortcut icon" href="favicon.ico" type="image/x-icon">`
3.  如今还有很多其他的图标类型（详见[原文](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E5%9C%A8%E4%BD%A0%E7%9A%84%E7%AB%99%E7%82%B9%E5%A2%9E%E5%8A%A0%E8%87%AA%E5%AE%9A%E4%B9%89%E5%9B%BE%E6%A0%87)）可以考虑。

## 应用CSS和JavaScript

```html
<link rel="stylesheet" href="my-css-file.css"><!-- rel就是relation,stylesheet就是样式表 -->
<script src="my-js-file.js"></script><!-- 放在文件头的尾部 -->
<!-- 这俩都可以直接插入在其中，不用引入文件 -->
```

## 主语言
为了视障人士，很有必要这样写：

```html
<html lang="zh-CN"></html>
```

其它部分的语言可以在各自部分的属性设置。另外，[更多参考](https://www.w3.org/International/articles/language-tags/)。

# 文字（语义）格式
合理的内容结构化会使读者的阅读体验更轻松，更愉快；可以让搜索引擎等工作更好；可以有助于视力障碍者使用屏幕阅读器；可以有助于CSS和JavaScript定位等。所以：

* 只对每个页面使用一次`<h1>`，其他标题位于下方。
* 如果内容复杂，不如分成多个页面。

语义有助于浏览器正确识别内容类型。

## 列表(List)
列表可以嵌套。列表的类型大致有三种：

### 无序列表(UnOrderList)

```html
<ul>
  <li>豆浆</li>
  <li>油条</li>
  <li>豆汁</li>
  <li>焦圈</li>
</ul>
```
### 有序列表(Orderlist)

```html
<ol>
  <li>沿着条路走到头</li>
  <li>右转</li>
  <li>直行穿过第一个十字路口</li>
  <li>在第三个十字路口处左转</li>
  <li>继续走 300 米，学校就在你的右手边</li>
</ol>
```

### 描述列表(Description List)
浏览器的默认样式会在**描述术语**（description terms）和**描述列表的描述部分**（description description）之间产生缩进。

```html
<dl>
  <dt>培根</dt>
    <dd>整个世界的粘合剂。</dd>
  <dt>鸡蛋</dt>
    <dd>一块蛋糕的粘合剂。</dd>
  <dt>咖啡</dt>
    <dd>一种浅棕色的饮料。</dd>
    <dd>可以在清晨带来活力。</dd>
</dl>
```

## 超链接
前面有关于`<a>超链接</a>`元素及其介绍。几乎任何网络内容都可以转换为链接，点击超链接将转到另一个网址，使网络成为互联网。
要注意[绝对链接和相对链接](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E7%BB%9D%E5%AF%B9url%E5%92%8C%E7%9B%B8%E5%AF%B9url)。为了使用屏幕阅读器的用户，要使用清晰的链接措辞，链接文本要简短说明内容，不要裸出链接，不要说废话，比如“这里有一个链接：”[尽可能使用相对链接](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E5%B0%BD%E5%8F%AF%E8%83%BD%E4%BD%BF%E7%94%A8%E7%9B%B8%E5%AF%B9%E9%93%BE%E6%8E%A5)，留下链接时要留下[清晰的指示](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E9%93%BE%E6%8E%A5%E5%88%B0%E9%9D%9Ehtml%E8%B5%84%E6%BA%90_%E2%80%94%E2%80%94%E7%95%99%E4%B8%8B%E6%B8%85%E6%99%B0%E7%9A%84%E6%8C%87%E7%A4%BA)。

```html
<a href="../../../complex/path/to/my/file.html" title="支持复杂路径">可以指向特定文件地址</a>

<h2 id="Mailing_address">先标记一个文档片段</h2>
<p>可以引用 <a href="#Mailing_address">本地文档片段</a>。</p>
<p>或<a href="contacts.html#Mailing_address">其它</a>。</p>
<a href="https://download.mozilla.org/?product=firefox-latest-ssl&os=win64&lang=zh-CN" download="firefox-latest-64bit-installer.exe">下载最新的 Firefox 中文版 - Windows（64位）</a>
```

此外还有[邮件链接](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#%E7%94%B5%E5%AD%90%E9%82%AE%E4%BB%B6%E9%93%BE%E6%8E%A5)。

## 引用

```html
<blockquote cite="引用地址">
    <p>块引用。（里面一定要有元素吗？文字呢？）</p>
</blockquote>
<p>行内引用<q cite="引用地址">就好看多了</q></p>
<!-- 这俩一个是块级元素，一个是内联元素 -->
<p>如果你想让被引用的内容来源显示或者读出来，可以用<cite>来源</cite>显示出来，也可以在外面套上链接。</p>
```

## 缩略语

```html
<p><abbr title="美国国家航空航天局（National Aeronautics and Space Administration）">NASA</abbr> 做了一些动人心弦的事情。</p>
```

## 上标和下标

```html
<p>化学和数学用<sup>上标</sup>和<sub>下标</sub>很方便。</p>
```

## [联系方式](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E6%A0%87%E8%AE%B0%E8%81%94%E7%B3%BB%E6%96%B9%E5%BC%8F)、[计算机代码](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E5%B1%95%E7%A4%BA%E8%AE%A1%E7%AE%97%E6%9C%BA%E4%BB%A3%E7%A0%81)、[时间和日期](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/Advanced_text_formatting#%E6%A0%87%E8%AE%B0%E6%97%B6%E9%97%B4%E5%92%8C%E6%97%A5%E6%9C%9F)
见标题链接中的源网址。

# 网页结构

```html
<main> 存放每个页面独有的内容。
<article>包围的内容即一篇文章，与页面其它部分无关。
<section>与<article>类似，但<section>更适用于组织页面使其按功能（比如迷你地图、一组文章标题和摘要）分块。
<aside>侧边栏，多嵌套于<article>中。
<header> （全网页或<article>或<section>等的）页眉，
<nav>导航栏，不应包含二级链接。
<footer>页脚。
```

# 无语义元素

```html
<div>块级无语义元素，容易被滥用导致网页难以维护</div>
<span>内联无语义元素</span>
<br>换行</br>
<hr><!--分割线-->
```
