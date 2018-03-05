
CSS值的类型有很多种，常见如下：  

* 数值： 长度值，用于指定例如元素宽度，边框宽度，字体大小以及无单位整数用于指定相对线宽或运行动画的次数。
* 百分比： 可以用于指定尺寸或长度，例如相对于父容器的长度或高度或默认的字体大小。
* 颜色：用于指定背景颜色，字体颜色
* 坐标位置： 例如用于指定定位元素相对于屏幕的左上方的位置
* 函数：用于指定背景图片或背景图片渐变

## 数值
### 长度和尺寸
在CSS布局、排版等等的所有时候，你都会使用到长度/尺寸单位，如下：

```
<p>This is a paragraph.</p>
<p>This is a paragraph.</p>
<p>This is a paragraph.</p>
```
```
p {
  margin: 5px;
  padding: 10px;
  border: 2px solid black;
  background-color: cyan;
}

p:nth-child(1) {
  width: 150px;
  font-size: 18px;
}

p:nth-child(2) {
  width: 250px;
  font-size: 24px;
}

p:nth-child(3) {
  width: 350px;
  font-size: 30px;
}
```

像素px是一种绝对单位，因为无论其他相关的设置怎么变化，像素指定的值是不会变化的。其他的绝对单位如下：

* mm, cm, in: 毫米（Millimeters），厘米（centimeters），英寸（inches）
* pt, pc: 点（Points (1/72 of an inch)）， 十二点活字（ picas (12 points.)）

相对单位： 他们是相对于当前元素的字号（ font-size ）或者视口（viewport ）尺寸。 

* `em`: 1em与当前元素的字体大小相同（更具体地说，一个大写字母M的宽度）。CSS样式被应用之前，浏览器给网页设置的默认基础字体大小是16像素，这意味着对一个元素来说1em的计算值默认为16像素。但是要小心—em单位是会继承父元素的字体大小，所以如果在父元素上设置了不同的字体大小，em的像素值就会变得复杂。现在不要过于担心这个问题，我们将在后面的文章和模块中更详细地介绍继承和字体大小设置。em是Web开发中最常用的相对单位。
* `ex`，`ch`: 分别是小写x的高度和数字0的宽度。这些并不像em那样被普遍使用或很好地被支持。
* `rem`: REM（root em）和em以同样的方式工作，但它总是等于默认基础字体大小的尺寸；继承的字体大小将不起作用，这听起来像一个更好的选择比em，虽然在旧版本的IE上不被支持
* `vw`,`vh`: 分别是视口宽度的1/100和视口高度的1/100，其次，它不像rem那样被广泛支持。

### 无单位的值

让一个元素完全去除外边框和内边框，可以只使用无单位的0

```
margin: 0;
```
### 无单位的行高
`line-height`, 设置元素中每行文本的高度。

```
<p>Blue ocean silo royal baby space glocal evergreen relationship housekeeping
native.</p>
```
```
p {
/*这里的font-size的值为16px; 行高为1.5或24px。*/
  line-height: 1.5;
}
```

### 动画的数值
CSS动画能够让页面上的HTML元素动起来。下面的例子，当我们把鼠标浮动到一个段落上的时候，它能够旋转起来：

```
<p>Hello</p>
```
```
@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

p {
  color: red;
  width: 100px;
  font-size: 40px;
  transform-origin: center;
}

p:hover {
  animation-name: rotate;
  animation-duration: 0.6s;
  animation-timing-function: linear;
  animation-iteration-count: 5;
}
```

## 百分比
可以使用百分比值指定可以通过特定数值指定的大部分内容.

```
<div>Fixed width layout with pixels</div>
<div>Liquid layout with percentages</div>
```
```
div {
  margin: 10px;
  font-size: 200%;
  color: white;
  height: 150px;
  border: 2px solid black;
}

div:nth-child(1) {
  background-color: red;
  width: 650px;
}

div:nth-child(2) {
  background-color: blue;
  width: 75%;
}
```

## 颜色
CSS中指定颜色的方法有很多
### 关键词
有大约165个不同的关键字可用于现代Web浏览器

```
<p>This paragraph has a red background</p>
```

```
p {
  background-color: red;
}
```

### 十六进制值

```
p:nth-child(1) {
  background-color: #ff0000;
}
```

### RGB

```
p:nth-child(1) {
  background-color: rgb(255,0,0);
}
```

### RGBA 

```
p:nth-child(1) {
  background-color: rgba(255,0,0,0.5);
  position: relative;
  top: 30px;
  left: 50px;
}
```

### 透明度

```
/* Red with RGBA */
p:nth-child(1) {
  background-color: rgba(255,0,0,0.5);
}

/* Red with opacity */
p:nth-child(2) {
  background-color: rgb(255,0,0);
  opacity: 0.5;
}
```

## 函数

```
/* calculate the new position of an element after it has been rotated by 45 degress */
transform: rotate(45deg);
/* calculate the new position of an element after it has been moved across 50px and down 60px */
transform: translate(50px, 60px);
/* calculate the computed value of 90% of the current width minus 15px */
width: calc(90%-15px);
/* fetch an image from the network to be used as a background image */
background-image: url('myimage.png');
```



