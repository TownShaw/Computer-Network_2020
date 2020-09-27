<center><b><font size = 6>CSS学习笔记</font></b></center>
<p align = 'right'>肖桐 PB18000037</p>

本文摘抄自[菜鸟教程](https://www.runoob.com/css/css-tutorial.html)

`CSS`即层叠样式表(Cascading Style Sheets)。样式表定义如何显示`HTML`元素，就像`HTML`中的字体标签和颜色属性所起的作用那样。

# 一、`CSS`语法

## 1. `CSS`规则

`CSS`规则由两个主要的部分构成：选择器，以及一条或多条声明。如：

```css
h1 {color:blue; font-size:12px;}
```

选择器通常是需要改变样式的`HTML`元素。每条声明由一个属性和一个值组成(类似于`HTML`中标签的属性)，属性和值被冒号分开(`HTML`中用等号分开)。

[CSS选择器参考手册](https://www.runoob.com/cssref/css-selectors.html)	[CSS属性参考](https://www.runoob.com/cssref/css-reference.html)	[CSS单位](https://www.runoob.com/cssref/css-units.html)

`CSS`声明总是以分号(;)结束，声明总是以大括号({ })括起来。

## 2. `CSS`注释

`CSS`注释以`/*`开始，以`*/`结束(类似`C`)。

# 二、`CSS`选择器

[CSS选择器参考手册](https://www.runoob.com/cssref/css-selectors.html)

## 1. `id`选择器

`id`选择器可以为标有特定`id`的`HTML`元素指定特定的样式。

`HTML`元素以`id`属性来设置`id`选择器，`CSS`中`id`选择器以`#`来定义。如以下的样式规则应用于元素属性`id="para1"`：

```css
#para1 {text-align:center; color:red;}
```

## 2. `class`选择器

`class`选择器用于描述一组元素的样式，`class`选择器有别于id选择器，**`class`可以在多个元素中使用。**

`class`选择器在`HTML`中以`class`属性表示, 在`CSS`中，类选择器以一个点`.`号显示：

在以下的例子中，所有拥有`center`类的`HTML`元素均为居中。

```css
.center {text-align:center;}
```

也可以指定**特定的`HTML`元素使用`class`。**

在以下实例中, 所有的`p`元素使用`class="center"`让该元素的文本居中:

```css
p.center {text-align:center;}
```

# 三、`CSS`创建

当读到一个样式表时，浏览器会根据它来格式化`HTML`文档。

## 1. 如何插入样式表

### (1). 外部样式表

通过使用`<link>`标签链接到(导入)样式表。`<link>`标签应该在头部使用：

```html
<head>
    <link rel="stylesheet" type="text/css" href="mystyle.css">	<!-- rel属性和type属性有什么用？ -->
</head>
```

### (2). 内部样式表

当文档需要特殊的样式时，可以使用内部样式表。使用`<style>`标签在文档头部定义内部样式表，如：

```html
<head>
    <style>
        hr {color:sienna;}
        p {margin-left:20px;}
        body {background-image:url("images/back40.gif")}
    </style>
</head>
```

### (3). 内联样式

当样式仅需要在一个元素上应用一次时可用内联样式。要使用内联样式，可在相关的标签内使用`style`属性，`style`属性可以包含任何`CSS`属性，如：

```html
<p style="color:sienna; margin-left=20px">这是一个段落</p>
```

### (4). 多重样式

如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从**更具体的样式表**中被继承过来。 

例如，**外部样式表**拥有针对`h3`选择器的三个属性：

```css
h3
{
	color:red;
    text-align:left;
    font-size:8pt;
}
```

而内部样式表拥有针对 h3 选择器的两个属性：

```css
h3
{
    text-align:right;
    font-size:20pt;
}
```

假如拥有内部样式表的这个页面同时与外部样式表链接，那么 h3 得到的样式是：

```css
h3
{
    color:red;
    text-align:right;
    font-size:20pt;
}
```

即颜色属性将被继承于外部样式表，而文字排列（text-alignment）和字体尺寸（font-size）会被内部样式表中的规则取代。(因为内部样式表更"具体"，优先级更高。)

一般情况下，优先级如下：

**（内联样式）Inline style > （内部样式）Internal style sheet >（外部样式）External style sheet > 浏览器默认样式**

# 四、`CSS`背景

`CSS`背景属性用于定义`HTML`元素的背景。

[CSS背景](https://www.runoob.com/css/css-background.html)

## 1. 背景颜色

`background-color`属性定义了元素的背景颜色。

页面的背景颜色使用在`body`的选择器中：

```css
body {background-color:#b0c4de}
```

`CSS`中，颜色值可以以以下方式定义：

- 十六进制 - 如：`"#ff0000"`
- RBG - 如：`"rgb(255, 0, 0)"`
- 颜色名称 - 如：`red`

## 2. 背景图像

`background-image`属性描述了元素的背景图像。

默认情况下，背景图像进行平铺重复显示，以覆盖整个元素实体。如：

```css
body {background-image:url('paper.gif');}
```

### (1). 水平或垂直平铺

默认情况下`background-image`属性会在页面的水平或者垂直方向平铺。

设置图像只在水平方向平铺：

```css
body
{
    background-image:url("...");
    background-repeat:repeat-x;
    /* 在垂直方向平铺则是 repeat-y, 不平铺则是 no-repeat*/
}
```

### (2). 设置位置

以上实例中，背景图像与文本显示在同一个位置，为了让页面排版更加合理，不影响文本的阅读，我们可以改变图像的位置。

可以利用`background-position`属性改变图像在背景中的位置：

```css
body
{
    background-image:url("...");
    background-repeat:no-repeat;
    background-position:right top;
}
```

### (3). 简写属性

我们也可以将以上的属性合并在同一个属性中，背景颜色的简写属性为`background`。如：

```css
body {background: #ffffff url("...") no-repeat right top;}	/* 分别为颜色、图像、平铺、位置 */
```

简写时的属性值顺序为：

- `background-color`
- `background-image`
- `background-repeat`
- `background-attachment`
- `background-position`

# 五、`CSS`文本格式

[CSS文本格式](https://www.runoob.com/css/css-text.html)

## 1. 文本修饰

`text-decoration`属性用来设置或删除文本的装饰。

从设计的角度看`text-decoration`属性主要是用来删除链接的下划线：

```css
a {text-decoration:none;}
```

也可以用来装饰文字：

```css
h1 {text-decoration:overline;}
h2 {text-decoration:line-through;}
h3 {text-decoration:underline;}
```

## 2. 文本转换

文本转换属性是用来指定在一个文本中的大写和小写字母。

可用于所有字句变成大写或小写字母，或每个单词的首字母大写。如：

```css
p.uppercase {text-transform:uppercase;}	/* 通过class属性使用 如<p class="uppercase">...</p> */
p.lowercase {text-transform:lowercase;}
p.capitalize {text-transform:capitalize;}	/* 有什么用？ */
```

## 3. 文本缩进

文本缩进属性是用来指定文本的第一行的缩进：

```css
p {text-indent:50px;}
```

## 4. 指定文本之间的空间

### (1). 字符之间的空间

使用`letter-spacing`属性来指定字符之间的空间：

```css
h1 {letter-spacing:2px;}
h2 {letter-spacing:-3px;}
```

汉字之间的空间也是使用`letter-space`属性进行调整的。

### (2). 行与行之间的空间

`line-height`属性用于决定行与行之间的空间，如：

```css
p.small {line-height:70%;}
p.big {line-height:200%;}
```

### (3). 单词之间的空间

`word-spacing`属性用于修改单词之间的空间，如：

```css
p {word-spacing:30px;}
```

## 5. 文本阴影

`text-shadow`用于设置文本阴影，如：

```css
h1 {text-shadow:2px 2px 0px #FF0000;}	/* 实际上就是将改变颜色之后的字体进行偏移, 第一个长度表示左右偏移, 第二个长度表示上下偏移, 第三个单位表示阴影的模糊程度 */
```

# 六、`CSS`字体

[CSS字体](https://www.runoob.com/css/css-font.html)

## 1. `CSS`字体系列

`font-family`属性用于设置文本的字体系列。如：

```css
p {font-family:"Times New Roman", "Times", "serif";}
```

# 七、`CSS`链接

[CSS链接](https://www.runoob.com/css/css-link.html)

四个链接状态：

- `a:link` - 正常，未访问过的链接
- `a:visited` - 用户已访问过的链接
- `a:hover` - 当用户鼠标放在链接上时
- `a:active` - 链接被点击的那一刻

可设置这四种状态的链接颜色：

```css
a:link {color:#000000;}
a:visited {color:#00FF00;}
a:hover {color:#FF00FF;}
a:active {color:#0000FF;}
```

当设置为若干链路状态的样式，也有一些顺序规则：

- `a:hover`必须跟在`a:link`和`a:visited`之后
- `a:active`必须跟在`a:hover`后面

也可以删除或修改链接的下划线，通过`text-decoration`属性实现。如：

```css
a:link {text-decoration:none;}
a:visited {text-decoration:none;}
a:hover {text-decoration:underline;}
a:active {text-decoration:underline;}
```

还可以通过属性`background-color`改变链接背景颜色，如：

```css
a:link {background-color:#B2FF99;}
a:visited {background-color:#FFFF85;}
a:hover {background-color:#FF704D;}
a:active {background-color:#FF704D;}
```

# 八、`CSS`列表

[CSS列表](https://www.runoob.com/css/css-list.html)

## 1. 不同的列表项标记

`list-style-type`属性指定列表项标记的类型是：

```css
ul.a {list-style-type:circle;}
ul.b {list-style-type: square;}
 
ol.c {list-style-type: upper-roman;}
ol.d {list-style-type: lower-alpha;}
```

## 2. 作为列表项标记的图像

可以使用属性`list-style-image`属性将列表项标记改为图像：

```css
ul {list-style-image:url("sqpurple.gif");}
```

# 九、`CSS`表格

# 十、`CSS`盒子模型

[CSS盒子模型](https://www.runoob.com/css/css-boxmodel.html)

`CSS`盒模型本质上是一个盒子，封装周围的`HTML`元素，它包括：

- `Margin`外边距 -  清除边框外的区域，外边距是透明的。

- `Border`边框 - 围绕在内边距和内容外的边框。

- `Padding`填充(内边距) - 清除内容周围的区域，内边距是透明的。

- `Content`实际内容 - 盒子的内容，显示文本和图像。

![](D:\Codes\HTML\image\1.png)


元素的宽度和高度

通过对`div`标签进行配置，可以达到指定元素宽度和高度的目的，如：

```css
div
{
    width: 220px;	/* 内容(content)的宽度 */
    padding: 10px;	/* 内容距离两边界的宽度, 内边距 */
    border: 5px solid gray;	/* 边距宽度 */
    margin: 0px;	/*  */
}
/* 上边距和下边距？ */
```

总元素宽度的计算方法：$总元素宽度 = width + 2 * padding + 2 * border + 2 * margin$

## 1. `CSS border`边框

[CSS边框](https://www.runoob.com/css/css-border.html)

### (1). `CSS`边框样式

`CSS`边框属性允许指定一个元素边框的样式和颜色。通过`border-style`属性来指定。有：

```css
border-style:none;	/* 无边框 */
border-style:dotted;	/* 定义一个点线边框 */
border-style:dashed;	/* 定义一个虚线边框 */
border-style:solid;	/* 定义实线边框 */
border-style:double;	/* 定义两个边框, 两个边框的宽度与 border-width 的值相同 */
border-style:groove;	/* 定义3D沟槽边框, 可指定边框颜色 */
border-style:ridge;	/* 定义3D脊边框, 可指定边框颜色 */
border-style:inset;	/* 定义一个3D的嵌入边框, 可指定边框颜色 */
border-style:outset;	/* 定义一个3D突出边框, 可指定颜色 */
```

边框颜色可以通过`border-color`属性决定。

### (2). 边框宽度

可以通过`border-width`属性来为边框指定宽度。如：

```css
p.one
{
    border-style:solid;
    border-width:5px;
}
p.two
{
    border-style:solid;
    border-width:medium;	/* 3个关键字: thick, medium, thin */
}
```

### (3). 单独设置各边

可以指定不同的侧边不同的边框，如：

```css
p
{
    border-top-style:dotted;
    border-right-style:solid;
    border-bottom-style:dotted;
    border-left-style:solid;
}
```

可见，可通过附加`top、right、bottom、left`来改变特定边的属性。`border-width、border-color`也相同。

## 2. `CSS outline`轮廓

[CSS轮廓](https://www.runoob.com/css/css-outline.html)

轮廓`(outline)`是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。通过`outline-color、outline-style、outline-width`属性来决定轮廓样式。如：

```css
p
{
    outline-color:red;
    outline-style:none;	/* 样式和CSS边框相同 */
    outline-width:2px;
}
```

## 3. `CSS margin`外边距

[CSS margin](https://www.runoob.com/css/css-margin.html)

margin 清除周围的（外边框）元素区域。margin 没有背景颜色，是完全透明的。

margin 可以单独改变元素的上，下，左，右边距，也可以一次改变所有的属性。

Q：有什么用？怎么用？

A：

### (1). 单边外边距属性

类似于`CSS border`，可以使用`top、bottom、left、right`指定不同侧面不同的边距。如：

```css
p.margin
{
    margin-top:100px;
    margin-bottom:100px;
    margin-left:50px;
    margin-right:50px;
}
```

## 4. `CSS padding`填充

[CSS填充](https://www.runoob.com/css/css-padding.html)

当元素的 padding（填充）内边距被清除时，所释放的区域将会受到元素背景颜色的填充。

单独使用 padding 属性可以改变上下左右的填充。

### (1). 单边内边距属性 
如同`CSS border`边框一样，使用`top、bottom、left、right`可以改变四个方向的填充大小。如：

```css
p.padding
{
    padding-top:25px;
    padding-bottom:25px;
    padding-left:50px;
    padding-right:50px;
}
```

# 十一、`CSS`分组和嵌套选择器 
[CSS分组和嵌套选择器](https://www.runoob.com/css/css-grouping-nesting.html)

## 1. 分组选择器 
在 CSS 中有很多具有相同样式的元素，为避免以下冗长的代码：

```css
h1 {color:green;}
h2 {color:green;}
p {color:green;}
```

可以使用以下写法：

```css
h1,h2,p {color:green;}
```

## 2. 嵌套选择器

它可能适用于选择器内部的选择器的样式。

- `p {}` 为所有`p`元素指定一个样式

- `.marked {}`为所有`class="marked"`的元素指定一个样式
- `.marked p {}`为所有`class="marked"`元素内的`p`元素指定一个样式
- `p.marked {}`为所有`class="marked"`的`p`元素指定一个样式

如：

```css
<head>
<style>
p
{
    color:blue;
    text-align:center;
}
.marked
{
    background-color:red;
}
.marked p
{
    color:white;
}
p.marked{
    text-decoration:underline;
}
</style>
</head>
<body>
<p>这个段落是蓝色文本，居中对齐。</p>
<div class="marked">
<p>这个段落不是蓝色文本。</p>
</div>
<p>所有 class="marked"元素内的 p 元素指定一个样式，但有不同的文本颜色。</p>
    
<p class="marked">带下划线的 p 段落。</p>
</body>
```

# 十二、`CSS`尺寸

# 十三、`CSS`显示(Display)和可见性(Visibility)

[CSS显示和可见性](https://www.runoob.com/css/css-display-visibility.html)

## 1. 隐藏元素

`display`属性设置一个元素应如何显示，`visibility`属性指定一个元素应可见还是隐藏。

`visibility:hidden`可以隐藏某个元素，但隐藏的元素**仍需占用与未隐藏之前一样的空间。**也就是说，该元素虽然被隐藏了，但仍然会影响布局。如：

```css
h1.hidden {visibility:hidden;}
```

`display:none`可以隐藏某个元素，且**隐藏的元素不会占用任何空间。**也就是说，该元素不但被隐藏了，而且该元素原本占用的空间也会从页面布局中消失。如：

```css
h1.hidden {display:none;}
```

## 2. `CSS Display` - 块和行内元素

块元素是一个元素，占用了全部宽度，在前后都是换行符。

块元素拥有如下特点：

1. 每个块级元素都是独自占一行
2. 元素的高度、宽度、行高和边距都是可以设置的
3. 元素的宽度如果不设置的话，默认为父元素的宽度

块元素的例子：

- `<h1>`
- `<p>`
- `<div>`

行内元素只需要必要的宽度，不强制换行。

行内元素的特点：

1. 每一个行内元素可以和别的行内元素共享一行，相邻的行内元素会排列在同一行里，直到一行排不下了，才会换行。
2. 行内元素设置`width, height`无效，宽度随元素的内容而变化。
3. 行内水平方向的`padding-left`和`padding-right`都会产生边距效果，但是竖直方向上的`padding-top`和`padding-bottom`都不会产生边距效果。

行内元素的例子：

- `<span>`
- `<a>`

## 3. 改变元素显示

可以更改行内元素和块元素，反之亦然，可以使页面看起来是以一种特定的方式组合，并仍然遵循web标准。

下面的示例把列表项显示为行内元素：

```css
li {display:inline;}
```

下面的示例把span元素作为块元素：

```css
span {display:block;}
```

