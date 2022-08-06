# HTML 笔记

## HTML 简介

### HTML 解析

![img](https://www.runoob.com/wp-content/uploads/2013/06/02A7DD95-22B4-4FB9-B994-DDB5393F7F03.jpg)

- **\<!DOCTYPE html>** 声明为 HTML5 文档
- **\<html>** 元素是 HTML 页面的根元素
- **\<head>** 元素包含了文档的元（meta）数据，如 **\<meta charset="utf-8">** 定义网页编码格式为 **utf-8**。
- **\<title>** 元素描述了文档的标题
- **\<body>** 元素包含了可见的页面内容
- **\<h1>** 元素定义一个一级标题
- **\<p>** 元素定义一个段落

**注：** 在浏览器的页面上使用键盘上的 F12 按键（Mac fn+F12）开启调试模式，就可以看到组成标签。

### 构建 DOM 树

DOM（Document Object Model）文档对象模型，是 HTML 和 XML 文档的编程接口。

DOM 以树结构表达 HTML 文档，树的每个分支的终点都是一个节点，每个节点都包含着对象。

DOM 将 web 页面与脚本或编程语言链接起来，可以通过 DOM 提供的方法改变节点的结构、样式或者内容。

![image-20220723154750984](/Users/zaizai/Library/Application Support/typora-user-images/image-20220723154750984.png)

### 什么是 HTML

HTML 是用来描述网页的一种语言。

- HTML 指的是超文本标记语言: **H**yper**T**ext **M**arkup **L**anguage
- HTML 不是一种编程语言，而是一种**标记**语言
- 标记语言是一套**标记标签** (markup tag)
- HTML 使用标记标签来**描述**网页
- HTML 文档包含了HTML **标签**及**文本**内容
- HTML文档也叫做 **web 页面**

### HTML 标签

HTML 标记标签通常被称为 HTML 标签 (HTML tag)。

- HTML 标签是由 *尖括号* 包围的关键词，比如 \<html>
- HTML 标签通常是 *成对出现* 的，比如 \<b> 和 \</b>
- 标签对中的第一个标签是 *开始标签* ，第二个标签是 *结束标签* 
- 开始和结束标签也被称为  *开放标签*  和 *闭合标签*

### HTML 元素

"HTML 标签" 和 "HTML 元素" 通常都是描述同样的意思。

但是严格来讲, 一个 HTML 元素包含了开始标签与结束标签，如下实例:

HTML 元素:

```html
<p>这是一个段落。</p>
```

### Web 浏览器

Web浏览器（如谷歌浏览器，Internet Explorer，Firefox，Safari）是用于读取HTML文件，并将其作为网页显示。

浏览器并不是直接显示的HTML标签，但可以使用标签来决定如何展现HTML页面的内容给用户。

## HTML 基础

### HTML 标题

HTML 标题（Heading）是通过\<h1> - \<h6> 标签来定义的。

```html
<h1>这是一个标题</h1> 
<h2>这是一个标题</h2> 
<h3>这是一个标题</h3>
```

### HTML 段落

HTML 段落是通过标签 \<p> 来定义的。

```html
<p>这是一个段落。</p> 
<p>这是另外一个段落。</p>
```

### HTML 链接

HTML 链接是通过标签 \<a> 来定义的。

```html
<a href="https://www.runoob.com">这是一个链接</a>
```

**提示：**在 href 属性中指定链接的地址。

### HTML 图像

HTML 图像是通过标签 \<img> 来定义的.

```html
<img src="/images/logo.png" width="258" height="39" />
```

**注意：**图像的名称和尺寸是以属性的形式提供的。

### HTML 内容划分

<img src="/Users/zaizai/Library/Application Support/typora-user-images/image-20220723194847239.png" alt="image-20220723194847239" style="zoom:50%;" />

## HTML 元素

### HTML 元素语法

- HTML 元素以**开始标签**起始
- HTML 元素以**结束标签**终止
- **元素的内容**是开始标签与结束标签之间的内容
- 某些 HTML 元素具有**空内容（empty content）**
- 空元素**在开始标签中进行关闭**（以开始标签的结束而结束）
- 大多数 HTML 元素可拥有**属性**
- 某些**属性值**可以省略

**不要忘记结束标签**

即使您忘记了使用结束标签，大多数浏览器也会正确地显示 HTML：

```html
<p>这是一个段落
<p>这是一个段落
```

以上实例在浏览器中也能正常显示，因为关闭标签是可选的。

但不要依赖这种做法。忘记使用结束标签会产生不可预料的结果或错误。

### HTML 空元素

没有内容的 HTML 元素被称为空元素。空元素是在开始标签中关闭的。

\<br> 就是没有关闭标签的空元素（\<br> 标签定义换行）。

在 XHTML、XML 以及未来版本的 HTML 中，所有元素都必须被关闭。

在开始标签中添加斜杠，比如 \<br />，是关闭空元素的正确方法，HTML、XHTML 和 XML 都接受这种方式。

即使 \<br> 在所有浏览器中都是有效的，但使用 \<br /> 其实是更长远的保障。

**HTML 提示：使用小写标签**

HTML 标签对大小写不敏感：\<P> 等同于 \<p>。许多网站都使用大写的 HTML 标签。

菜鸟教程使用的是小写标签，因为万维网联盟（W3C）在 HTML 4 中**推荐**使用小写，而在未来 (X)HTML 版本中**强制**使用小写。

## HTML 属性

属性是 HTML 元素提供的附加信息。

### HTML 属性

- HTML 元素可以设置**属性**
- 属性可以在元素中添加**附加信息**
- 属性一般描述于**开始标签**
- 属性总是以名称/值对的形式出现，**比如：name="value"**。

### 属性实例

HTML 链接由 \<a> 标签定义。链接的地址在 **href 属性**中指定：

```html
<a href="http://www.runoob.com">这是一个链接</a>
```

### HTML 属性常用引用属性值

属性值应该始终被包括在引号内。

双引号是最常用的，不过使用单引号也没有问题。

**提示：**在某些个别的情况下，比如属性值本身就含有双引号，那么您必须使用单引号，例如：name='John "ShotGun" Nelson'

### HTML 提示：使用小写属性

属性和属性值对大小写不敏感。

不过，万维网联盟在其 HTML 4 推荐标准中推荐小写的属性/属性值。

而新版本的 (X)HTML 要求使用小写属性。

### HTML 属性参考手册

下面列出了适用于大多数 HTML 元素的属性：

| 属性  | 描述                                                         |
| :---- | :----------------------------------------------------------- |
| class | 为 html 元素定义一个或多个类名（classname）(类名从样式文件引入) |
| id    | 定义元素的唯一 id                                            |
| style | 规定元素的行内样式（inline style）                           |
| title | 描述了元素的额外信息 (作为工具条使用)                        |

## HTML 标题

在 HTML 文档中，标题很重要。

### HTML 标题

标题（Heading）是通过 \<h1> - \<h6> 标签进行定义的。

\<h1> 定义最大的标题。 \<h6> 定义最小的标题。

```html
<h1>这是一个标题。</h1> 
<h2>这是一个标题。</h2> 
<h3>这是一个标题。</h3>
```

**注释：**浏览器会自动地在标题的前后添加空行。

### 标题很重要

请确保将 HTML 标题 标签只用于标题。不要仅仅是为了生成**粗体**或**大号**的文本而使用标题。

搜索引擎使用标题为您的网页的结构和内容编制索引。

因为用户可以通过标题来快速浏览您的网页，所以用标题来呈现文档结构是很重要的。

应该将 h1 用作主标题（最重要的），其后是 h2（次重要的），再其次是 h3，以此类推。

### HTML 水平线

\<hr> 标签在 HTML 页面中创建水平线。

hr 元素可用于分隔内容。

```html
<p>这是一个段落。</p> 
<hr> 
<p>这是一个段落。</p> 
<hr> 
<p>这是一个段落。</p>
```

### HTML 注释

可以将注释插入 HTML 代码中，这样可以提高其可读性，使代码更易被人理解。浏览器会忽略注释，也不会显示它们。

注释写法如下:

```html
<!-- 这是一个注释 -->
```

**注释：**开始括号之后（左边的括号）需要紧跟一个叹号 **!** (英文标点符号)，结束括号之前（右边的括号）不需要，合理地使用注释可以对未来的代码编辑工作产生帮助。

### HTML 提示 - 如何查看源代码

你是否看过一些网页然后惊叹它是如何实现的。

如果您想找到其中的奥秘，只需要单击右键，然后选择"查看源文件"（IE）或"查看页面源代码"（Firefox），其他浏览器的做法也是类似的。这么做会打开一个包含页面 HTML 代码的窗口。

## HTML 段落

HTML 可以将文档分割为若干段落。

段落是通过 \<p> 标签定义的。

```html
<p>这是一个段落 </p> 
<p>这是另一个段落</p>
```

**注意：**浏览器会自动地在段落的前后添加空行。（\</p> 是块级元素）

### 不要忘记结束标签

即使忘了使用结束标签，大多数浏览器也会正确地将 HTML 显示出来：

```html
<p>这是一个段落 
<p>这是另一个段落
```

上面的例子在大多数浏览器中都没问题，但不要依赖这种做法。忘记使用结束标签会产生意想不到的结果和错误。

### HTML 折行

如果您希望在不产生一个新段落的情况下进行换行（新行），请使用 **\<br>** 标签：

```
<p>这个<br>段落<br>演示了分行的效果</p>
```

\<br /> 元素是一个空的 HTML 元素。由于关闭标签没有任何意义，因此它没有结束标签。

### HTML 输出- 使用提醒

我们无法确定 HTML 被显示的确切效果。屏幕的大小，以及对窗口的调整都可能导致不同的结果。

对于 HTML，您无法通过在 HTML 代码中添加额外的空格或换行来改变输出的效果。

当显示页面时，浏览器会移除源代码中多余的空格和空行。所有连续的空格或空行都会被算作一个空格。需要注意的是，HTML 代码中的所有连续的空行（换行）也被显示为一个空格。

## HTML 文本格式化

### HTML 文本格式化标签

| 标签      | 描述         |
| :-------- | :----------- |
| \<b>      | 定义粗体文本 |
| \<em>     | 定义着重文字 |
| \<i>      | 定义斜体字   |
| \<small>  | 定义小号字   |
| \<strong> | 定义加重语气 |
| \<sub>    | 定义下标字   |
| \<sup>    | 定义上标字   |
| \<ins>    | 定义插入字   |
| \<del>    | 定义删除字   |

### HTML "计算机输出" 标签

| 标签    | 描述               |
| :------ | :----------------- |
| \<code> | 定义计算机代码     |
| \<kbd>  | 定义键盘码         |
| \<samp> | 定义计算机代码样本 |
| \<var>  | 定义变量           |
| \<pre>  | 定义预格式文本     |

### HTML 引文, 引用, 及标签定义

| 标签          | 描述               |
| :------------ | :----------------- |
| \<abbr>       | 定义缩写           |
| \<address>    | 定义地址           |
| \<bdo>        | 定义文字方向       |
| \<blockquote> | 定义长的引用       |
| \<q>          | 定义短的引用语     |
| \<cite>       | 定义引用、引证     |
| \<dfn>        | 定义一个定义项目。 |

## HTML 链接

HTML 使用超级链接与网络上的另一个文档相连。几乎可以在所有的网页中找到链接。点击链接可以从一张页面跳转到另一张页面。

### HTML 超链接（链接）

HTML使用标签 \<a>来设置超文本链接。

超链接可以是一个字，一个词，或者一组词，也可以是一幅图像，您可以点击这些内容来跳转到新的文档或者当前文档中的某个部分。

当您把鼠标指针移动到网页中的某个链接上时，箭头会变为一只小手。

在标签 \<a> 中使用了 href 属性来描述链接的地址。

默认情况下，链接将以以下形式出现在浏览器中：

- 一个未访问过的链接显示为蓝色字体并带有下划线。
- 访问过的链接显示为紫色并带有下划线。
- 点击链接时，链接显示为红色并带有下划线。

### HTML 链接语法

链接的 HTML 代码很简单。它类似这样：

```html
<a href="url">链接文本</a>
```

href 属性描述了链接的目标。

**提示:** *"链接文本"* 不必一定是文本。图片或其他 HTML 元素都可以成为链接。

### HTML 链接 - target 属性

使用 target 属性，你可以定义被链接的文档在何处显示。

下面的这行会在新窗口打开文档：

```html
<a href="https://www.runoob.com/" target="_blank" rel="noopener noreferrer">访问菜鸟教程!</a>
```

### HTML 链接- id 属性

id 属性可用于创建一个 HTML 文档书签。

**提示：**书签不会以任何特殊方式显示，即在 HTML 页面中是不显示的，所以对于读者来说是隐藏的。

在 HTML 文档中插入 ID:

```html
<a id="tips">有用的提示部分</a>
```

在 HTML 文档中创建一个链接到 "有用的提示部分(id="tips")"：

```html
<a href="#tips">访问有用的提示部分</a>
```

或者，从另一个页面创建一个链接到"有用的提示部分(id="tips")"：

```html
<a href="https://www.runoob.com/html/html-links.html#tips">访问有用的提示部分</a>
```

### 基本的注意事项 - 有用的提示

**注释：** 请始终将正斜杠添加到子文件夹。假如这样书写链接：href="https://www.runoob.com/html"，就会向服务器产生两次 HTTP 请求。这是因为服务器会添加正斜杠到这个地址，然后创建一个新的请求，就像这样：href="https://www.runoob.com/html/"。

## HTML 头部

### HTML \<head> 元素

\<head> 元素包含了所有的头部标签元素。在 \<head>元素中你可以插入脚本（scripts）, 样式文件（CSS），及各种meta信息。

可以添加在头部区域的元素标签为: \<title>, \<style>, \<meta>, \<link>, \<script>, \<noscript> 和 \<base>。

### HTML \<title> 元素

\<title> 标签定义了不同文档的标题。

\<title> 在 HTML/XHTML 文档中是必须的。

\<title> 元素:

- 定义了浏览器工具栏的标题
- 当网页添加到收藏夹时，显示在收藏夹中的标题
- 显示在搜索引擎结果页面的标题

一个简单的 HTML 文档:

```html
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>文档标题</title>
</head>
 
<body>
文档内容......
</body>
 
</html>
```

### HTML \<base> 元素

\<base> 标签描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的默认链接:

```html
<head>
<base href="http://www.runoob.com/images/" target="_blank">
</head>
```

### HTML \<link> 元素

\<link> 标签定义了文档与外部资源之间的关系。

\<link> 标签通常用于链接到样式表:

```html
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

### HTML \<style> 元素

\<style> 标签定义了HTML文档的样式文件引用地址.

在 \<style> 元素中你也可以直接添加样式来渲染 HTML 文档:

```html
<head>
<style type="text/css">
body {background-color:yellow}
p {color:blue}
</style>
</head>
```

### HTML \<meta> 元素

meta 标签描述了一些基本的元数据。

\<meta> 标签提供了元数据，元数据也不显示在页面上，但会被浏览器解析。

META 元素通常用于指定网页的描述，关键词，文件的最后修改时间，作者，和其他元数据。

元数据可以使用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他Web服务。

\<meta> 一般放置于 \<head> 区域

#### \<meta> 标签- 使用实例

为搜索引擎定义关键词:

```html
<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">
```

为网页定义描述内容:

```html
<meta name="description" content="免费 Web & 编程 教程">
```

定义网页作者:

```html
<meta name="author" content="Runoob">
```

每30秒钟刷新当前页面:

```html
<meta http-equiv="refresh" content="30">
```

### HTML \<script> 元素

\<script>标签用于加载脚本文件，如： JavaScript。

\<script> 元素在以后的章节中会详细描述。

## HTML 样式 - CSS

CSS (Cascading Style Sheets) 用于渲染 HTML 元素标签的样式。

<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
</head>
<body>
</div>
</body>
</html>


<div style="opacity:0.5;position:absolute;left:50px;width:300px;height:150px;background-color:#40B3DF"></div>

<div style="font-family:verdana;padding:20px;border-radius:10px;border:10px solid #EE872A;">

<div style="opacity:0.3;position:absolute;left:120px;width:100px;height:200px;background-color:#8AC007"></div>

<h3>Look! Styles and colors</h3>

<div style="letter-spacing:12px;">Manipulate Text</div>

<div style="color:#40B3DF;">Colors
<span style="background-color:#B4009E;color:#ffffff;">Boxes</span>
</div>

<div style="color:#000000;">and more...</div>

### 如何使用CSS

CSS 是在 HTML 4 开始使用的,是为了更好的渲染HTML元素而引入的.

CSS 可以通过以下方式添加到 HTML 中:

- 内联样式- 在 HTML 元素中使用 "style" **属性**
- 内部样式表 -在 HTML 文档头部 \<head> 区域使用 \<style> **元素** 来包含 CSS
- 外部引用 - 使用外部 CSS **文件**

最好的方式是通过外部引用 CSS 文件.

在本站的 HTML 教程中我们使用了内联 CSS 样式来介绍实例，这是为了简化的例子，也使得你能更容易在线编辑代码并在线运行实例。

### 内联样式

当特殊的样式需要应用到个别元素时，就可以使用内联样式。 使用内联样式的方法是在相关的标签中使用样式属性。样式属性可以包含任何 CSS 属性。以下实例显示出如何改变段落的颜色和左外边距。

```html
<p style="color:blue;margin-left:20px;">这是一个段落。</p>
```

学习更多样式，请访问 [CSS 教程](https://www.runoob.com/css/)。

### HTML样式实例 - 背景颜色

背景色属性（background-color）定义一个元素的背景颜色：

```html
<body style="background-color:yellow;"> 
    <h2 style="background-color:red;">这是一个标题</h2> 
    <p style="background-color:green;">这是一个段落。</p> 
</body>
```

### HTML 样式实例 - 字体, 字体颜色 ，字体大小

我们可以使用 font-family（字体），color（颜色），和 font-size（字体大小）属性来定义字体的样式:

```html
<h1 style="font-family:verdana;">一个标题</h1> 
<p style="font-family:arial;color:red;font-size:20px;">一个段落。</p>
```

### HTML 样式实例 - 文本对齐方式

使用 text-align（文字对齐）属性指定文本的水平与垂直对齐方式：

```html
<h1 style="text-align:center;">居中对齐的标题</h1> 
<p>这是一个段落。</p>
```

PS：文本对齐属性 text-align取代了旧标签 \<center> 。

### 内部样式表

当单个文件需要特别样式时，就可以使用内部样式表。你可以在 \<head> 部分通过 \<style> 标签定义内部样式表:

```html
<head>
<style type="text/css">
body {background-color:yellow;}
p {color:blue;}
</style>
</head>
```

### 外部样式表

当样式需要被应用到很多页面的时候，外部样式表将是理想的选择。使用外部样式表，你就可以通过更改一个文件来改变整个站点的外观。

```html
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

### 已弃用的标签和属性

在 HTML 4, 原来支持定义 HTML 元素样式的标签和属性已被弃用。这些标签将不支持新版本的 HTML 标签。

不建议使用的标签有: \<font>, \<center>, \<strike>

不建议使用的属性: color 和 bgcolor.

## HTML 图像

![Pulpit Rock](https://www.runoob.com/images/pulpit.jpg)

### HTML 图像- 图像标签（ \<img>）和源属性（\src）

在 HTML 中，图像由 \<img> 标签定义。

\<img> 是空标签，意思是说，它只包含属性，并且没有闭合标签。

要在页面上显示图像，你需要使用源属性（src）。src 指 "source"。源属性的值是图像的 URL 地址。

**定义图像的语法是：**

```html
<img src="url" alt="some_text">
```

URL 指存储图像的位置。如果名为 "pulpit.jpg" 的图像位于 www.runoob.com 的 images 目录中，那么其 URL 为 [http://www.runoob.com/images/pulpit.jpg](https://www.runoob.com/images/pulpit.jpg)。

浏览器将图像显示在文档中图像标签出现的地方。如果你将图像标签置于两个段落之间，那么浏览器会首先显示第一个段落，然后显示图片，最后显示第二段。

### HTML 图像- Alt属性

alt 属性用来为图像定义一串预备的可替换的文本。

替换文本属性的值是用户定义的。

```html
<img src="boat.gif" alt="Big Boat">
```

在浏览器无法载入图像时，替换文本属性告诉读者她们失去的信息。此时，浏览器将显示这个替代性的文本而不是图像。为页面上的图像都加上替换文本属性是个好习惯，这样有助于更好的显示信息，并且对于那些使用纯文本浏览器的人来说是非常有用的。

### HTML 图像- 设置图像的高度与宽度

height（高度） 与 width（宽度）属性用于设置图像的高度与宽度。

属性值默认单位为像素:

```html
<img src="pulpit.jpg" alt="Pulpit rock" width="304" height="228">
```

**提示：**指定图像的高度和宽度是一个很好的习惯。如果图像指定了高度宽度，页面加载时就会保留指定的尺寸。如果没有指定图片的大小，加载页面时有可能会破坏 HTML 页面的整体布局。

### 基本的注意事项 - 有用的提示：

**注意：**假如某个 HTML 文件包含十个图像，那么为了正确显示这个页面，需要加载 11 个文件。加载图片是需要时间的，所以我们的建议是：慎用图片。

**注意：**加载页面时，要注意插入页面图像的路径，如果不能正确设置图像的位置，浏览器无法加载图片，图像标签就会显示一个破碎的图片。

## HTML 多媒体

\<audio>用于播放网络上的音频，\<video>用于播放网络上的视频，controls用于显示控制面板

```html
<audio src="name.ogg" controls></audio>
<video src="example.webm" controls></video>
```

## HTML 表格

### HTML 表格实例

| First Name | Last Name | Points |
| :--------- | :-------- | :----- |
| Jill       | Smith     | 50     |
| Eve        | Jackson   | 94     |
| John       | Doe       | 80     |
| Adam       | Johnson   | 67     |

### HTML 表格

表格由 \<table> 标签来定义。每个表格均有若干行（由 \<tr> 标签定义），每行被分割为若干单元格（由 \<td> 标签定义）。字母 td 指表格数据（table data），即数据单元格的内容。数据单元格可以包含文本、图片、列表、段落、表单、水平线、表格等等。

#### 表格实例

```html
<table border="1">
    <tr>
        <td>row 1, cell 1</td>
        <td>row 1, cell 2</td>
    </tr>
    <tr>
        <td>row 2, cell 1</td>
        <td>row 2, cell 2</td>
    </tr>
</table>
```

#### HTML 表格和边框属性

如果不定义边框属性，表格将不显示边框。有时这很有用，但是大多数时候，我们希望显示边框。

使用边框属性来显示一个带有边框的表格：

```
<table border="1">     
	<tr>         
		<td>Row 1, cell 1</td>         
		<td>Row 1, cell 2</td>     
	</tr> 
</table>
```

#### HTML 表格表头

表格的表头使用 \<th> 标签进行定义。

大多数浏览器会把表头显示为粗体居中的文本：

```html
<table border="1">     
    <tr>         
        <th>Header 1</th>         
        <th>Header 2</th>     
    </tr>     
    <tr>         
        <td>row 1, cell 1</td>         
        <td>row 1, cell 2</td>     
    </tr>     
    <tr>         
        <td>row 2, cell 1</td>         
        <td>row 2, cell 2</td>     
    </tr> 
</table>
```

## HTML 列表

### HTML无序列表

无序列表是一个项目的列表，此列项目使用粗体圆点（典型的小黑圆圈）进行标记。

无序列表使用 \<ul> 标签

```html
<ul>
  <li>Coffee</li>
  <li>Milk</li>
</ul>
```

浏览器显示如下：

- Coffee
- Milk

### HTML 有序列表

同样，有序列表也是一列项目，列表项目使用数字进行标记。 有序列表始于 \<ol> 标签。每个列表项始于 \<li> 标签。

列表项使用数字来标记。

```html
<ol>
<li>Coffee</li>
<li>Milk</li>
</ol>
```

浏览器中显示如下：

1. Coffee
2. Milk

### HTML 自定义列表

自定义列表不仅仅是一列项目，而是项目及其注释的组合。

自定义列表以 \<dl> 标签开始。每个自定义列表项以 \<dt> 开始。每个自定义列表项的定义以 \<dd> 开始。

```html
<dl>
  <dt>Coffee</dt>
  <dd>- black hot drink</dd>
  <dt>Milk</dt>
  <dd>- white cold drink</dd>
</dl>
```

浏览器显示如下：

- Coffee

    - black hot drink

- Milk

    - white cold drink

------

### 注意事项 - 有用提示

**提示：**列表项内部可以使用段落、换行符、图片、链接以及其他列表等等。

### 附录

ul 是 unordered lists 的缩写 (无序列表)

li 是 list item 的缩写 （列表项目）

ol 是 ordered lists 的缩写（有序列表）

dl 是 definition lists 的英文缩写 (自定义列表)

dt 是 definition term 的缩写 (自定义列表组)

dd 是 definition description 的缩写（自定义列表描述）

nl 是 navigation lists 的英文缩写 （导航列表）

tr 是 table row 的缩写 （表格中的一行）

th 是 table header cell 的缩写 （表格中的表头）

td 是 table data cell 的缩写 （表格中的一个单元格）

## HTML 区块

### HTML \<div> 和 \<span>

HTML 可以通过 \<div> 和 \<span>将元素组合起来。

### HTML 区块元素

大多数 HTML 元素被定义为**块级元素**或**内联元素**。

块级元素在浏览器显示时，通常会以新行来开始（和结束）。

实例: \<h1>, \<p>, \<ul>, \<table>

### HTML 内联元素

内联元素在显示时通常不会以新行开始。

实例: \<b>, \<td>, \<a>, \<img>

### HTML \<div> 元素

HTML \<div> 元素是块级元素，它可用于组合其他 HTML 元素的容器。

<div> 元素没有特定的含义。除此之外，由于它属于块级元素，浏览器会在其前后显示折行。

如果与 CSS 一同使用，\<div> 元素可用于对大的内容块设置样式属性。

\<div> 元素的另一个常见的用途是文档布局。它取代了使用表格定义布局的老式方法。使用 \<table> 元素进行文档布局不是表格的正确用法。\<table> 元素的作用是显示表格化的数据。

### HTML \<span> 元素

HTML \<span> 元素是内联元素，可用作文本的容器。

\<span> 元素也没有特定的含义。

当与 CSS 一同使用时，\<span> 元素可用于为部分文本设置样式属性。

## HTML 布局

网页布局对改善网站的外观非常重要。

请慎重设计您的网页布局。

### 在线实例

[使用 div 元素的网页布局](https://www.runoob.com/try/try.php?filename=tryhtml_layout_divs)
如何使用 \<div> 元素添加布局。

[使用 table 元素的网页布局](https://www.runoob.com/try/try.php?filename=tryhtml_layout_tables)
如何使用 \<table> 元素添加布局。

### 网站布局

大多数网站会把内容安排到多个列中（就像杂志或报纸那样）。

大多数网站可以使用 \<div> 或者 \<table> 元素来创建多列。CSS 用于对元素进行定位，或者为页面创建背景以及色彩丰富的外观。

虽然我们可以使用 HTML table 标签来设计出漂亮的布局，但是 table 标签是不建议作为布局工具使用的 - 表格不是布局工具。 

### HTML 布局 - 使用 \<div> 元素

div 元素是用于分组 HTML 元素的块级元素。

下面的例子使用五个 div 元素来创建多列布局：

### 实例

```html
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
</head>
<body>
 
<div id="container" style="width:500px">
 
<div id="header" style="background-color:#FFA500;">
<h1 style="margin-bottom:0;">主要的网页标题</h1></div>
 
<div id="menu" style="background-color:#FFD700;height:200px;width:100px;float:left;">
<b>菜单</b><br>
HTML<br>
CSS<br>
JavaScript</div>
 
<div id="content" style="background-color:#EEEEEE;height:200px;width:400px;float:left;">
内容在这里</div>
 
<div id="footer" style="background-color:#FFA500;clear:both;text-align:center;">
版权 © runoob.com</div>
 
</div>
 
</body>
</html>
```

### HTML 布局 - 使用表格

使用 HTML \<table> 标签是创建布局的一种简单的方式。

大多数站点可以使用 \<div> 或者 \<table> 元素来创建多列。CSS 用于对元素进行定位，或者为页面创建背景以及色彩丰富的外观。

即使可以使用 HTML 表格来创建漂亮的布局，但设计表格的目的是呈现表格化数据 - 表格不是布局工具！

下面的例子使用三行两列的表格 - 第一和最后一行使用 colspan 属性来横跨两列：

```html
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
</head>
<body>
 
<table width="500" border="0">
<tr>
<td colspan="2" style="background-color:#FFA500;">
<h1>主要的网页标题</h1>
</td>
</tr>
 
<tr>
<td style="background-color:#FFD700;width:100px;">
<b>菜单</b><br>
HTML<br>
CSS<br>
JavaScript
</td>
<td style="background-color:#eeeeee;height:200px;width:400px;">
内容在这里</td>
</tr>
 
<tr>
<td colspan="2" style="background-color:#FFA500;text-align:center;">
版权 © runoob.com</td>
</tr>
</table>
 
</body>
</html>
```

### HTML 布局 - 有用的提示

使用 CSS 最大的好处是，如果把 CSS 代码存放到外部样式表中，那么站点会更易于维护。通过编辑单一的文件，就可以改变所有页面的布局。如需学习更多有关 CSS 的知识，请访问我们的 [CSS 教程](https://www.runoob.com/css/css-tutorial.html)。

由于创建高级的布局非常耗时，使用模板是一个快速的选项。通过搜索引擎可以找到很多免费的网站模板（您可以使用这些预先构建好的网站布局，并优化它们）。

## HTML 表单

### HTML 表单和输入

HTML 表单用于收集不同类型的用户输入。

### HTML 表单

表单是一个包含表单元素的区域。

表单元素是允许用户在表单中输入内容,比如：文本域 (textarea)、下拉列表、单选框 (radio-buttons)、复选框 (checkboxes) 等等。

表单使用表单标签  \<form> 来设置:

```html
<form>
.
*input 元素*
.
</form>
```

### HTML 表单 - 输入元素

多数情况下被用到的表单标签是输入标签（\<input>）。

输入类型是由类型属性（type）定义的。大多数经常被用到的输入类型如下：

#### 文本域（Text Fields）

文本域通过 \<input type="text"> 标签来设定，当用户要在表单中键入字母、数字等内容时，就会用到文本域。

```html
<form>
First name: <input type="text" name="firstname"><br>
Last name: <input type="text" name="lastname">
</form>
```

浏览器显示效果如下：

<form>
First name: <input type="text" name="firstname"><br>
Last name: <input type="text" name="lastname">
</form>

**注意：**表单本身并不可见。同时，在大多数浏览器中，文本域的默认宽度是 20 个字符。

#### 密码字段

密码字段通过标签 \<input type="password"> 来定义:

```html
<form>
Password: <input type="password" name="pwd">
</form>
```

浏览器显示效果如下：

<form>
Password: <input type="password" name="pwd">
</form>

**注意：**密码字段字符不会明文显示，而是以星号或圆点替代。

#### 单选按钮（Radio Buttons）

\<input type="radio"> 标签定义了表单单选框选项

```html
<form>
<input type="radio" name="sex" value="male">Male<br>
<input type="radio" name="sex" value="female">Female
</form>
```

浏览器显示效果如下：

<form>
<input type="radio" name="sex" value="male">Male<br>
<input type="radio" name="sex" value="female">Female
</form>

#### 复选框（Checkboxes）

\<input type="checkbox"> 定义了复选框. 用户需要从若干给定的选择中选取一个或若干选项。

```html
<form>
<input type="checkbox" name="vehicle" value="Bike">I have a bike<br>
<input type="checkbox" name="vehicle" value="Car">I have a car
</form>
```

浏览器显示效果如下：

<form>
<input type="checkbox" name="vehicle" value="Bike">I have a bike<br>
<input type="checkbox" name="vehicle" value="Car">I have a car
</form>

#### 提交按钮 (Submit Button)

\<input type="submit"> 定义了提交按钮.

当用户单击确认按钮时，表单的内容会被传送到另一个文件。表单的动作属性定义了目的文件的文件名。由动作属性定义的这个文件通常会对接收到的输入数据进行相关的处理。:

<form name="input" action="html_form_action.php" method="get">
Username: <input type="text" name="user">
<input type="submit" value="Submit">
</form>

假如您在上面的文本框内键入几个字母，然后点击确认按钮，那么输入数据会传送到 "html_form_action.php" 的页面。该页面将显示出输入的结果。

## HTML 框架

**iframe 语法:**

```html
<iframe src="URL"></iframe>
```

该 URL 指向不同的网页。

### iframe - 设置高度与宽度

height 和 width 属性用来定义iframe标签的高度与宽度。

属性默认以像素为单位, 但是你可以指定其按比例显示 (如："80%")。

```html
<iframe loading="lazy" src="demo_iframe.htm" width="200" height="200"></iframe>
```

### iframe - 移除边框

frameborder 属性用于定义 iframe 表示是否显示边框。

设置属性值为 "0" 移除iframe的边框:

```html
<iframe src="demo_iframe.htm" frameborder="0"></iframe>
```

### 使用 iframe 来显示目标链接页面

iframe 可以显示一个目标链接的页面

目标链接的属性必须使用 iframe 的属性，如下实例:

```html
<iframe src="demo_iframe.htm" name="iframe_a"></iframe> 
<p><a href="https://www.runoob.com" target="iframe_a" rel="noopener">RUNOOB.COM</a></p>
```

## HTML 颜色

HTML 颜色由红色、绿色、蓝色混合而成。

### 颜色值

HTML 颜色由一个十六进制符号来定义，这个符号由红色、绿色和蓝色的值组成（RGB）。

每种颜色的最小值是0（十六进制：#00）。最大值是255（十六进制：#FF）。

#### 1600 万种不同颜色

三种颜色 红，绿，蓝的组合从 0 到 255，一共有 1600 万种不同颜色 (256 x 256 x 256)。

### Web安全色?

数年以前，当大多数计算机仅支持 256 种颜色的时候，一系列 216 种 Web 安全色作为 Web 标准被建议使用。其中的原因是，微软和 Mac 操作系统使用了 40 种不同的保留的固定系统颜色（双方大约各使用 20 种）。

我们不确定如今这么做的意义有多大，因为越来越多的计算机有能力处理数百万种颜色，不过做选择还是你自己。

最初，216 跨平台 web 安全色被用来确保：当计算机使用 256 色调色板时，所有的计算机能够正确地显示所有的颜色。

## HTML 颜色名

### 目前所有浏览器都支持以下颜色名

141 个颜色名称是在 HTML 和 CSS 颜色规范定义的（17 标准颜色，再加 124）。下表列出了所有颜色的值，包括十六进制值。

17 标准颜色：黑色，蓝色，水，紫红色，灰色，绿色，石灰，栗色，海军，橄榄，橙，紫，红，白，银，蓝绿色，黄色。点击其中一个颜色名称（或一个十六进制值）就可以查看与不同文字颜色搭配的背景颜色。

### 按颜色名排序

[按十六进制的值排序](https://www.runoob.com/html/html-colorvalues.html)

单击一个颜色名或者 16 进制值，就可以查看与不同文字颜色搭配的背景颜色。

## HTML 颜色值

颜色由红(R)、绿(G)、蓝(B)组成。

### 颜色值

颜色值由十六进制来表示红、绿、蓝（RGB）。

每个颜色的最低值为 0 (十六进制为 00)，最高值为 255 (十六进制为 FF)。

十六进制值的写法为 # 号后跟三个或六个十六进制字符。

三位数表示法为：#RGB，转换为 6 位数表示为：#RRGGBB。

### 通过十六进制（Hex）的颜色值排序

[查看以颜色名称排序的颜色列表](https://www.runoob.com/html/html-colornames.html)

## HTML 脚本

JavaScript 使 HTML 页面具有更强的动态和交互性。

### HTML \<script> 标签

\<script> 标签用于定义客户端脚本，比如 JavaScript。

\<script> 元素既可包含脚本语句，也可通过 src 属性指向外部脚本文件。

JavaScript 最常用于图片操作、表单验证以及内容动态更新。

下面的脚本会向浏览器输出 "Hello World!" ：

```html
<script> 
    document.write("Hello World!"); 
</script>
```

### HTML \<noscript> 标签

\<noscript> 标签提供无法使用脚本时的替代内容，比方在浏览器禁用脚本时，或浏览器不支持客户端脚本时。

\<noscript> 元素可包含普通 HTML 页面的 body 元素中能够找到的所有元素。

只有在浏览器不支持脚本或者禁用脚本时，才会显示 \<noscript> 元素中的内容：

```html
<script>
document.write("Hello World!")
</script>
<noscript>抱歉，你的浏览器不支持 JavaScript!</noscript>
```

## JavaScript体验

JavaScript实例代码:

**JavaScript可以直接在HTML输出:**

```html
document.write("<p>这是一个段落。</p>");
```

**JavaScript事件响应:**

```html
<button type="button" onclick="myFunction()">点我！</button>
```

**JavaScript处理 HTML 样式:**

```html
document.getElementById("demo").style.color="#ff0000";
```

## HTML 字符实体

HTML 中的预留字符必须被替换为字符实体。

一些在键盘上找不到的字符也可以使用字符实体来替换。

### HTML 实体

在 HTML 中，某些字符是预留的。

在 HTML 中不能使用小于号（<）和大于号（>），这是因为浏览器会误认为它们是标签。

如果希望正确地显示预留字符，我们必须在 HTML 源代码中使用字符实体（character entities）。 字符实体类似这样：

```
&entity_name;
或
&#entity_number;
```

如需显示小于号，我们必须这样写：**\&it;** 或 **\&#60;** 或 **\&#060;**

使用实体名而不是数字的好处是，名称易于记忆。不过坏处是，浏览器也许并不支持所有实体名称（对实体数字的支持却很好）。

### 不间断空格

HTML 中的常用字符实体是不间断空格 (\&nbsp;)。

浏览器总是会截短 HTML 页面中的空格。如果您在文本中写 10 个空格，在显示该页面之前，浏览器会删除它们中的 9 个。如需在页面中增加空格的数量，您需要使用 \&nbsp; 字符实体。

### 结合音标符

发音符号是加到字母上的一个 "glyph(字形)"。

一些变音符号, 如 尖音符 ( ̀) 和 抑音符 ( ́) 。

变音符号可以出现字母的上面和下面，或者字母里面，或者两个字母间。

变音符号可以与字母、数字字符的组合来使用。

以下是一些实例:

| 音标符 | 字符 | Construct | 输出结果 |
| :----- | :--- | :-------- | :------- |
| ̀       | a    | a&#768;   | à        |
| ́       | a    | a&#769;   | á        |
| ̂       | a    | a&#770;   | â        |
| ̃       | a    | a&#771;   | ã        |
| ̀       | O    | O&#768;   | Ò        |
| ́       | O    | O&#769;   | Ó        |
| ̂       | O    | O&#770;   | Ô        |
| ̃       | O    | O&#771;   | Õ        |

### HTML 字符实体

实体名称对大小写敏感！

| 显示结果 | 描述        | 实体名称           | 实体编号 |
| :------- | :---------- | :----------------- | :------- |
|          | 空格        | \&nbsp;            | \&#160;  |
| <        | 小于号      | \&lt;              | \&#60;   |
| >        | 大于号      | \&gt;              | \&#62;   |
| &        | 和号        | \&amp;             | \&#38;   |
| "        | 引号        | \&quot;            | \&#34;   |
| '        | 撇号        | \&apos; (IE不支持) | \&#39;   |
| ￠       | 分          | \&cent;            | \&#162;  |
| £        | 镑          | \&pound;           | \&#163;  |
| ¥        | 人民币/日元 | \&yen;             | \&#165;  |
| €        | 欧元        | \&euro;            | \&#8364; |
| §        | 小节        | \&sect;            | \&#167;  |
| ©        | 版权        | \&copy;            | \&#169;  |
| ®        | 注册商标    | \&reg;             | \&#174;  |
| ™        | 商标        | \&trade;           | \&#8482; |
| ×        | 乘号        | \&times;           | \&#215;  |
| ÷        | 除号        | \&divide;          | \&#247;  |

## HTML URL

### HTML 统一资源定位器（Uniform Resource Locators）

URL 是一个网页地址。

URL 可以由字母组成，如 "runoob.com"，或互联网协议（IP）地址： 192.68.20.50。大多数人进入网站使用网站域名来访问，因为名字比数字更容易记住。

### URL - 统一资源定位器

Web 浏览器通过 URL 从 Web 服务器请求页面。

当您点击 HTML 页面中的某个链接时，对应的 \<a> 标签指向万维网上的一个地址。

一个统一资源定位器 (URL)  用于定位万维网上的文档。

一个网页地址实例： http://www.runoob.com/html/html-tutorial.html 语法规则:

```
scheme://host.domain:port/path/filename
```

说明:

- scheme - 定义因特网服务的类型。最常见的类型是 http

- host - 定义域主机（http 的默认主机是 www）

- domain - 定义因特网域名，比如 runoob.com

- :port - 定义主机上的端口号（http 的默认端口号是 80）

- path - 定义服务器上的路径（如果省略，则文档必须位于网站的根目录中）。

- filename - 定义文档/资源的名称

### 常见的 URL Scheme

以下是一些URL scheme：

| Scheme |        访问        |               用于...               |
| :----: | :----------------: | :---------------------------------: |
|  http  |   超文本传输协议   | 以 http:// 开头的普通网页。不加密。 |
| https  | 安全超文本传输协议 |    安全网页，加密所有信息交换。     |
|  ftp   |    文件传输协议    |    用于将文件下载或上传至网站。     |
|  file  |                    |         您计算机上的文件。          |

### URL 字符编码

URL 只能使用 [ASCII 字符集](https://www.runoob.com/tags/html-ascii.html).

来通过因特网进行发送。由于 URL 常常会包含 ASCII 集合之外的字符，URL 必须转换为有效的 ASCII 格式。

URL 编码使用 "%" 其后跟随两位的十六进制数来替换非 ASCII 字符。

URL 不能包含空格。URL 编码通常使用 + 来替换空格。

### URL 编码实例

| 字符 | URL 编码 |
| :--- | :------- |
| €    | %80      |
| £    | %A3      |
| ©    | %A9      |
| ®    | %AE      |
| À    | %C0      |
| Á    | %C1      |
| Â    | %C2      |
| Ã    | %C3      |
| Ä    | %C4      |
| Å    | %C5      |

如需完整的 URL 编码参考，请访问我们的 [URL 编码参考手册](https://www.runoob.com/tags/html-urlencode.html)。

## HTML 速查列表

HTML 速查列表. 你可以打印它，以备日常使用。

### HTML 基本文档

```html
<!DOCTYPE html> 
<html> 
    <head> 
        <title>文档标题</title> 
    </head> 
    <body> 
        可见文本... 
    </body> 
</html>
```

### 基本标签（Basic Tags）

```html
<h1>最大的标题</h1> 
<h2> . . . </h2> 
<h3> . . . </h3> 
<h4> . . . </h4> 
<h5> . . . </h5> 
<h6>最小的标题</h6>   

<p>这是一个段落。</p> 
<br> （换行） 
<hr> （水平线） 
<!-- 这是注释 -->
```

### 文本格式化（Formatting）

```html
<b>粗体文本</b> 
<code>计算机代码</code> 
<em>强调文本</em> 
<i>斜体文本</i> 
<kbd>键盘输入</kbd>  
<pre>预格式化文本</pre>
<small>更小的文本</small> 
<strong>重要的文本</strong>   

<abbr> （缩写） 
<address> （联系信息） 
<bdo> （文字方向） 
<blockquote> （从另一个源引用的部分） 
<cite> （短引用） 
<del> （删除的文本） 
<ins> （插入的文本） 
<sub> （下标文本） 
<sup> （上标文本）
```

### 链接（Links）

普通的链接：<a href="http://www.example.com/">链接文本</a> 图像链接： <a href="http://www.example.com/"><img src="URL" alt="替换文本"></a> 邮件链接： <a href="mailto:webmaster@example.com">发送e-mail</a> 书签： <a id="tips">提示部分</a> <a href="#tips">跳到提示部分</a>

```html
普通的链接：<a href="http://www.example.com/">链接文本</a> 
图像链接： <a href="http://www.example.com/"><img src="URL" alt="替换文本"></a> 
邮件链接： <a href="mailto:webmaster@example.com">发送e-mail</a> 书签： 
<a id="tips">提示部分</a> 
<a href="#tips">跳到提示部分</a>
```

### 图片（Images）

```html
<img loading="lazy" src="URL" alt="替换文本" height="42" width="42">
```

### 样式/区块（Styles/Sections）

```html
<style type="text/css">
h1 {color:red;} 
p {color:blue;}
</style> 
<div>文档中的块级元素</div> 
<span>文档中的内联元素</span>
```

### 无序列表

```
<ul>    
	<li>项目</li>    
	<li>项目</li> 
</ul>
```

### 有序列表

```
<ol>    
	<li>第一项</li>    
	<li>第二项</li> 
</ol>
```

### 定义列表

```
<dl>  
	<dt>项目 1</dt>    
		<dd>描述项目 1</dd>  
	<dt>项目 2</dt>    
		<dd>描述项目 2</dd> 
</dl>
```

### 表格（Tables）

```html
<table border="1">   
	<tr>     
		<th>表格标题</th>     
		<th>表格标题</th>   
	</tr>   
	<tr>     
		<td>表格数据</td>     
		<td>表格数据</td>   
	</tr> 
</table>
```

### 框架（Iframe）

```html
<iframe src="demo_iframe.htm"></iframe>
```

### 表单（Forms）

```html
<form action="demo_form.php" method="post/get"> 
    <input type="text" name="email" size="40" maxlength="50"> 	  <input type="password"> 
    <input type="checkbox" checked="checked"> 
    <input type="radio" checked="checked"> 
    <input type="submit" value="Send"> 
    <input type="reset"> 
    <input type="hidden"> 
    	<select> 
            <option>苹果</option> 
            <option selected="selected">香蕉</option> 
            <option>樱桃</option> 
    	</select> 
 	<textarea name="comment" rows="60" cols="20"></textarea>  </form>
```

### 实体（Entities）

```html
&lt; 等同于 < 
&gt; 等同于 > 
&#169; 等同于 ©
```

## HTML 标签简写及全称

下表列出了 HTML 标签简写及全称：

| 标签        | 英文全称                  | 中文说明                       |
| :---------- | :------------------------ | :----------------------------- |
| a           | Anchor                    | 锚                             |
| abbr        | Abbreviation              | 缩写词                         |
| acronym     | Acronym                   | 取首字母的缩写词               |
| address     | Address                   | 地址                           |
| alt         | alter                     | 替用(一般是图片显示不出的提示) |
| b           | Bold                      | 粗体（文本）                   |
| bdo         | Direction of Text Display | 文本显示方向                   |
| big         | Big                       | 变大（文本）                   |
| blockquote  | Block Quotation           | 区块引用语                     |
| br          | Break                     | 换行                           |
| cell        | cell                      | 巢                             |
| cellpadding | cellpadding               | 巢补白                         |
| cellspacing | cellspacing               | 巢空间                         |
| center      | Centered                  | 居中（文本）                   |
| cite        | Citation                  | 引用                           |
| code        | Code                      | 源代码（文本）                 |
| dd          | Definition Description    | 定义描述                       |
| del         | Deleted                   | 删除（的文本）                 |
| dfn         | Defines a Definition Term | 定义定义条目                   |
| div         | Division                  | 分隔                           |
| dl          | Definition List           | 定义列表                       |
| dt          | Definition Term           | 定义术语                       |
| em          | Emphasized                | 加重（文本）                   |
| font        | Font                      | 字体                           |
| h1~h6       | Header 1 to Header 6      | 标题1到标题6                   |
| hr          | Horizontal Rule           | 水平尺                         |
| href        | hypertext reference       | 超文本引用                     |
| i           | Italic                    | 斜体（文本）                   |
| iframe      | Inline frame              | 定义内联框架                   |
| ins         | Inserted                  | 插入（的文本）                 |
| kbd         | Keyboard                  | 键盘（文本）                   |
| li          | List Item                 | 列表项目                       |
| nl          | navigation lists          | 导航列表                       |
| ol          | Ordered List              | 排序列表                       |
| optgroup    | Option group              | 定义选项组                     |
| p           | Paragraph                 | 段落                           |
| pre         | Preformatted              | 预定义格式（文本 ）            |
| q           | Quotation                 | 引用语                         |
| rel         | Reload                    | 加载                           |
| s/ strike   | Strikethrough             | 删除线                         |
| samp        | Sample                    | 示例（文本                     |
| small       | Small                     | 变小（文本）                   |
| span        | Span                      | 范围                           |
| src         | Source                    | 源文件链接                     |
| strong      | Strong                    | 加重（文本）                   |
| sub         | Subscripted               | 下标（文本）                   |
| sup         | Superscripted             | 上标（文本）                   |
| td          | table data cell           | 表格中的一个单元格             |
| th          | table header cell         | 表格中的表头                   |
| tr          | table row                 | 表格中的一行                   |
| tt          | Teletype                  | 打印机（文本）                 |
| u           | Underlined                | 下划线（文本）                 |
| ul          | Unordered List            | 不排序列表                     |
| var         | Variable                  | 变量（文本）                   |

## HTML 总结

**你已经完成了 HTML 的学习，下一步该学习什么呢？**

### HTML 总结

本教程已教你如何使用 HTML 创建站点。

HTML 是一种在 Web 上使用的通用标记语言。HTML 允许你格式化文本，添加图片，创建链接、输入表单、框架和表格等等，并可将之存为文本文件，浏览器即可读取和显示。

HTML 的关键是标签，其作用是指示将出现的内容。

### 语义化的好处

HTML中的元素、属性及属性值都拥有某些含义，开发者应该遵循语义来编写HTML。

语义化的好处：

1. 代码可读性
2. 可维护性
3. 搜索引擎优化
4. 提升无障碍性
