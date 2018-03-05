#  前言
CSS页面布局技术允许我们拾取网页中的元素，并且控制它们相对正常布局流、周边元素、父容器或者主视口/窗口的位置。

常见的布局技术：

* 浮动
* 定位
* CSS表格
* 弹性盒子
* 网格

每种技术都有它们的用途，各有优缺点。

## 正常布局流

正常布局流是指在不对页面进行任何布局控制时，浏览器默认的HTML布局方式。

通过布局技术会覆盖默认的布局行为：

* position 属性 — 正常布局流中，默认为 static ，使用其它值会引起元素不同的布局方式，例如将元素固定到浏览器视口的左上角。
* 浮动——应用 float 值，诸如 left 能够让块级元素互相并排成一行，而不是一个堆叠在另一个上面。
* display 属性——标准值 block, inline or inline-block 会改变元素在正常布局流中的行为方式(见 Types of CSS boxes )，而一些不常见或特殊的值允许我们使用完全不同的方式进行布局，使用工具比如Flexbox。

## 浮动

浮动技术允许元素浮动到另外一个元素的左侧或右侧，而不是默认的一个堆叠另一个，在布局中被广泛的应用。最初，设计浮动时，其实并不是为了布局的，而是为了实现文字环绕的特效， 如图：
![](https://segmentfault.com/img/remote/1460000011358516?w=206&h=214)

float 属性有四个可能的值：

* left — 将元素浮动到左侧。
* right — 将元素浮动到右侧。
* none — 默认值, 不浮动。
* inherit — 继承父元素的浮动属性。

###  图片浮动

```
<h1>Simple float example</h1>

<img src="https://mdn.mozillademos.org/files/13340/butterfly.jpg" alt="A pretty butterfly with red, white, and brown coloring, sitting on a large leaf">

<p> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis, eget fermentum sapien.</p>

```

```
body {
  width: 90%;
  max-width: 900px;
  margin: 0 auto;
}

p {
  line-height: 2;
  word-spacing: 0.1rem;
}

img {
  float: left;
  margin-right: 30px;
}

```

浮动是如何工作的——浮动元素 (这个例子中的<img> 元素)会脱离正常的文档布局流，并吸附到其父容器的左边 (这个例子中的<body>元素)。在正常布局中位于该浮动元素之下的内容，此时会围绕着浮动元素，填满其右侧的空间。

## 定位

定位技术(position)的概念就是它允许你定义一个元素相对于其他正常元素的位置，这里的其他元素可以是父元素，另一个元素，甚至是浏览器窗口本身。

有5种主要的定位类型需要我们了解：

* 静态定位(Static positioning)是每个元素默认的属性——它表示“将元素放在文档布局流的默认位置——没有什么特殊的地方”。块级元素生成一个矩形框，作为文档流的一部分；行内元素则会创建一个或多个行框，置于其父元素中。

* 相对定位(Relative positioning)元素框相对于之前正常文档流中的位置发生偏移，并且原先的位置仍然被占据。发生偏移的时候，可能会覆盖其他元素。
* 绝对定位(Absolute positioning)将元素完全从页面的正常布局流中移出，类似将它单独放在一个图层中. 我们可以将元素相对于页面的 <html> 元素边缘固定，或者相对于离元素最近的被定位的祖先元素(ancestor element)。绝对定位在创建复杂布局效果时非常有用，例如通过标签显示和隐藏的内容面板或者通过按钮控制滑动到屏幕中的信息面板. 它是相对于包含块进行偏移(所谓的包含块就是最近一级外层元素position不为static的元素)
* 固定定位(Fixed positioning)与绝对定位非常类似，除了它是将一个元素相对浏览器视口固定，而不是相对另外一个元素。 在创建类似页面滚动总是处于页面上方的导航菜单时非常有用。
* sticky：(这是css3新增的属性值)粘性定位，官方的介绍比较简单，或许你不能理解。其实，它就相当于relative和fixed混合。最初会被当作是relative，相对于原来的位置进行偏移；一旦超过一定阈值之后，会被当成fixed定位，相对于视口进行定位

### 偏移量

`top`、`right`、`bottom`、`left` 这四个属性值是定位时的偏移量。偏移量不会对static的元素起到作用。

常用定位的偏移

* relative：它的偏移是相对于原先在文档流中的位置，如图
![](https://segmentfault.com/img/remote/1460000011358513?w=218&h=217)

> 这里设置了top：100px，left：100px。

* absolute：它的偏移量是相对于最近一级position不是static的祖先元素的
* fixed：它的偏移量是相对于视口的。

## 最初的布局 -- table

最初的时候，网页简单到可能只有文字和链接。这时候，大家最常用的就是table。因为table可以展示出多个块的排布。

这种布局现在应该不常用了，因为在形色单一时，使用起来方便。但是，现在的网页变得越来越复杂，适配的问题也是越来越多，这种布局已经不再时候了。

主要是div块的出现，可以使得网页进行灵活的排布，使得网页变得繁荣。这时，开发者也开始思索如何去更加清晰地分辨网页的层次。接下来，我们可以看看有哪些比较出名的布局方式。

## 两栏布局

![](https://segmentfault.com/img/remote/1460000011358519?w=1918&h=1006)

两栏布局：一栏定宽，一栏自适应。这样子做的好处是定宽的那一栏可以做广告，自适应的可以作为内容主体。

** 实现方式 **

1. float + margin

```
<body>
  <div class="left">定宽</div>
  <div class="right">自适应</div>
</body>
```

```
.left{
  width: 200px;
  height: 600px;
  background: red;
  float: left;
  display: table;
  text-align: center;
  line-height: 600px;
  color: #fff;
}

.right{
  margin-left: 210px;
  height: 600px;
  background: yellow;
  text-align: center;
  line-height: 600px;
}
```

2. 其他的方法：还可以使用position的absolute，可以使用同样的效果

## 三栏布局

它的特点：两边定宽，然后中间的width是auto的，可以自适应内容，再加上margin边距，来进行设定。

三栏布局可以有4种实现方式，每种实现方式都有各自的优缺点。

1. 使用左右两栏使用float属性，中间栏使用margin属性进行撑开，注意的是html的结果

```
<div class="left">左栏</div>
<div class="right">右栏</div>
<div class="middle">中间栏</div>
```

```
.left{
  width: 200px;height: 300px; background: yellow; float: left;    
}
.right{
  width: 150px; height: 300px; background: green; float: right;
}
.middle{
  height: 300px; background: red; margin-left: 220px; margin-right: 160px;
}
```

> 缺点是：1. 当宽度小于左右两边宽度之和时，右侧栏会被挤下去；2. html的结构不正确

2. 使用position定位实现，即左右两栏使用position进行定位，中间栏使用margin进行定位

```
<div class="left">左栏</div>
<div class="middle">中间栏</div>
<div class="right">右栏</div>
```

```
.left{
    background: yellow;
    width: 200px;
    height: 300px;
    position: absolute;
    top: 0;
    left: 0;
}
.middle{
    height: 300px;
    margin: 0 220px;
    background: red;
}
.right{
    height: 300px;
    width: 200px;
    position: absolute;
    top: 0;
    right: 0;
    background: green;
}
```

> 好处是：html结构正常。

> 缺点时：当父元素有内外边距时，会导致中间栏的位置出现偏差

3. 使用float和BFC配合圣杯布局

将middle的宽度设置为100%，然后将其float设置为left，其中的main块设置margin属性，然后左边栏设置float为left，之后设置margin为-100%，右栏也设置为float：left，之后margin-left为自身大小。

```
<div class="wrapper">
    <div class="middle">
        <div class="main">中间</div>
    </div>
    <div class="left">
        左栏
    </div>
    <div class="right">
        右栏
    </div>
</div>
```

```
.wrapper{
    overflow: hidden;  //清除浮动
}
.middle{
    width: 100%;
    float: left;
}
.middle .main{
    margin: 0 220px;
    background: red;
}
.left{
    width: 200px;
    height: 300px;
    float: left;
    background: green;
    margin-left: -100%;
}
.right{
    width: 200px;
    height: 300px;
    float: left;
    background: yellow;
    margin-left: -200px;
}

```

> 缺点是：1. 结构不正确 2. 多了一层标签

4. flex布局

```
<div class="wrapper">
    <div class="left">左栏</div>
    <div class="middle">中间</div>
    <div class="right">右栏</div>
</div>
```

```
.wrapper{
    display: flex;
}
.left{
    width: 200px;
    height: 300px;
    background: green;
}
.middle{
    width: 100%;
    background: red;
    marign: 0 20px;
}
.right{
    width: 200px;
    height: 3000px;
    background: yellow;
}
```

## 移动端

### 媒体查询

如果你需要一张网页能够在PC和移动端都能按照不同的设计稿显示出来，那么你需要做的就是去设置媒体查询。
媒体查询的css标识符是@media，它的媒体类型可以分为：

1. all， 所有媒体
2. braille 盲文触觉设备
3. embossed 盲文打印机
4. print 手持设备
5. projection 打印预览
6. screen 彩屏设备
7. speech ‘听觉’类似的媒体类型
8. tty 不适用像素的设备
9. tv 电视

```
@media screen {
  p.test {font-family:verdana,sans-serif;font-size:14px;}
}
@media print {
  p.test {font-family:times,serif;font-size:10px;}
}
@media screen,print {
  p.test {font-weight:bold;}
}
/*移动端样式*/
@media only screen and (min-device-width : 320px) and (max-device-width : 480px) {
  /* Styles */
}
```

```
@media screen and (min-width: 750px){
  .media{
    height: 100px;
    background: red;
  }
}

@media (max-width: 750px){
  .media{
    height: 200px;
    background: green;
  }
}
```

### flex布局

往往在移动端开发过程中，弹性布局是非常实用的一种手段。往往你并不需要去反复的使用媒体查询的。整整的响应式布局是使界面能够自动的根据屏幕进行变化，做到完美的弹性布局，在必要的时候，去使用媒体查询，对页面进行调整。本篇所讲述的正是，在移动端响应式布局当中被经过使用的一个东西flexbox(弹性盒子)

flex布局又被称为弹性布局。由容器和子项目组成。

何为容器，就是设定display为flex的地方。如图所示：
![](https://camo.githubusercontent.com/e189eab4096a782d319c77e36f12f38d8c2bad31/68747470733a2f2f6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031342f30352f666c65782d636f6e7461696e65722e737667)

而容器内部的直接子项就是`flex item`。
![](https://camo.githubusercontent.com/da68c54e9174e1cc5f7031b2895f9d0845854d65/68747470733a2f2f6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031342f30352f666c65782d6974656d732e737667)

在清楚了flex的结构划分之后，我们还要牢记的是flex的轴线(axis)。正如坐标系，具备着x轴与y轴，flex在整个布局当中，也可分为水平方向和垂直方向，简称为主轴和交叉轴，如图所示：

![](https://camo.githubusercontent.com/4a62f4e4c2c48901fe2e18f0937f52a0f872dedb/687474703a2f2f7777772e7275616e796966656e672e636f6d2f626c6f67696d672f61737365742f323031352f6267323031353037313030342e706e67)

整个图片上还有main start，就是项目到容器的开始位置，而main end，就是项目到容器结束的位置。同理，cross start和cross end就是交叉轴上面的开始和结束的位置。当然了，还有main size和cross size就是项目的水平距离和垂直距离。

### container基础属性值

> 1. display 表示容器展示的布局类型，可设定为flex和inline-flex。两者的设定也就是inline和block的区别。当然了，在webkit内核的浏览器(safari)中使用时，需要在其前面加上前缀(-webkit-flex)

```
.container{
    display: -webkit-flex;
    display: flex; /* or inline-flex*/
}
```

> 2. flex-direction 表示容器内部子项目的展示方向。它主要有四个方向 `row`,`row-reverse`,`column`,`column-reverse`，如图：

![](https://camo.githubusercontent.com/b0dfc73f89cdcdbf23c548ff4c41e2e65dd53d56/68747470733a2f2f6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031332f30342f666c65782d646972656374696f6e322e737667)


```
.container{
    flex-direction: row   /* 默认 行正序*/ ||  row-reverse /*行倒序*/ ||  column  /* 列正序*/ || column-reverse /*列倒序*/
}
```

> 3. flex-wrap 表示当容器内部内容超出容器时，容器是否分行展示。

![] (https://camo.githubusercontent.com/8729e7c09cbe6aa09f5bf30a81f43a67d38294d0/68747470733a2f2f6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031342f30352f666c65782d777261702e737667)

这个属性的值，有三种：`nowrap`(浏览器默认，不分行) 、`wrap`(超出的部分分行处理)、`wrap-reverse`(分行逆序)。

```
.container{
   flex-wrap: nowrap || wrap || wrap-reverse;
}
```

> 4. flex-flow: 这个属性就是可以将上面两个属性合起来写的属性，

```
.container{
     flex-flow: row  wrap;
}
```

> 5. justify-content: 表示容器内部的子项目的水平对齐方式。而水平的对齐方式主要有六种: flex-start、flex-end、center、space-between、space-around、space-evenly。

![](https://camo.githubusercontent.com/c613d849ca410ca11bb7b8a969130b4b1285e86b/68747470733a2f2f63646e2e6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031332f30342f6a7573746966792d636f6e74656e742d322e737667)

* flex-start：对应的对齐方式是水平向左对齐。（浏览器默认）
* flex-end：对应的对齐方式是水平向右对齐。
* center：对应的对齐方式是居中对齐。
* space-between： 对应的是，每个元素之间中间流出间隙是一样的，两边无间隙。
* space-around：对应的是，每个元素周围的间隙是一样的，而不是元素之间的，因此，可以从途中看出两边的间隙会比中间小一半。
* space-evenly：对应的是，每个元素之间的间隙大小一致。

> 6. align-items: 表示容器内部的子项目的垂直方向上的对齐方式。在垂直方向上的对齐方式有5种：flex-start、flex-end、center、stretch(浏览器默认)、baseline。

![](https://camo.githubusercontent.com/e01d135e6cb96b6b104e37a6d71c017476076afc/68747470733a2f2f63646e2e6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031342f30352f616c69676e2d6974656d732e737667)


* flex-start: 对应的对齐方式是垂直向上对齐。
* flex-end： 对应的对齐方式是垂直向下对齐。
* center：对应的对齐方式是垂直居中对齐。
* stretch：对应的对齐方式是将整个子项目的长度拉伸到最大块的高度(浏览器默认)
* baseline： 对应的对齐方式是子项目内部的文字基线对齐。


> 7. align-content: 表示在对行的情况下，每行所对应的垂直方向上的对齐方式。主要有六种对齐方式：flex-start、flex-end、center、stretch、space-between、space-around。

![](https://camo.githubusercontent.com/31f74b4857f1596c8666c9c09bdb64d734e65d91/68747470733a2f2f6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031332f30342f616c69676e2d636f6e74656e742e737667)

* flex-start：对应的是每一行在垂直方向上向上对齐的方式
* flex-end：对应的是每一行在垂直方向上向下对齐的方式
* center：对应的是每一行在垂直方向上居中对齐的方式
* stretch：对应的是每一行延展到铺满整个垂直方向。
* space-between：对应的就是每行之间留有空隙，而两边没有空隙
* space-around：对应的就是每行周围的空隙均相等

container的属性就是上述的7种，只要熟练的掌握这些属性，就能对整体容器进行一个基础的布局了。当然了，要改变内部子项目时，还得需要搞清楚子项目上面的几个属性。

下面，我们就来分析分析内部的子项目属性，可分为以下几个部分：

1. order：表示的是顺序，子项目的排列顺序。通常，默认情况下，子项目都是按照默认顺序进行排序的。但是，有时候你或许需要将后面的元素拿上来，那你就可以使用order这个属性，正如图中展示的：

![](https://camo.githubusercontent.com/e6e1e7ba543402aeaf112218bfe0fdebfd038ef8/68747470733a2f2f6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031332f30342f6f726465722d322e737667)

在css中的使用为：

```
  order: <integer>  //如1
```

2. flex-grow：表示的是元素的所占空间的比例，在设置每个元素flex-grow为1时，一行内的子元素都是均分的，即1：1：1。但是，如果你给第一个元素设置flex-grow为2时，它们的比例就会变成2：1：1。如图：

![](https://camo.githubusercontent.com/01daad62e322de3d0c4483210684ea8ea3bbbca3/68747470733a2f2f6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031342f30352f666c65782d67726f772e737667)

3. flex-shrink：表示子项目的伸缩

4. flex-basis: 表示子项目的长度，默认为auto，即当设置flex-grow时，长度就为flex-grow的value，如果没有，就是块本身内容的大小。

5. flex: 表示flex-grow、flex-shrink和flex-basis的集合写法，默认为0，1，auto

```
flex: <flex-grow> <flex-shrink> <flex-basis>
```

6. align-self：表示子项目在垂直轴线上的放置方式。

![](https://camo.githubusercontent.com/a9b0fd06176492d109a7fb5ea1aa1eab364e2c9b/68747470733a2f2f6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031342f30352f616c69676e2d73656c662e737667)

它的值也和align-items一样，flex-start、flex-end、center、stretch、baseline还有auto。默认为auto，即为容器的排列方式。


## 参考

[MDN-CSS教程](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Introduction)
[CSS布局说](https://segmentfault.com/a/1190000011358507)


## 其他

### 尺寸

* px
* 百分比：百分比的参照物是父元素，50%相当于父元素width的50%
* rem：这个对于复杂的设计图相当有用，它是html的font-size的大小
* em：它虽然也是一个相对的单位，相对于父元素的font-size，但是，并不常用，主要是计算太麻烦了。


### rem适配

rem可以说是移动端适配的一个神器。类似于手淘等界面，都是使用的rem进行的适配。这种界面有个特点就是页面元素的复杂度比较高，而使用flex进行布局会导致页面被拉伸，但是上下的高度却没有变化等问题。