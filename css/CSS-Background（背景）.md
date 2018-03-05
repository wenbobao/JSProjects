## CSS Background

CSS Background 属性用于定义HTML元素的背景。

### background-color

`background-color` 属于定义了元素的背景颜色。

```
body {background-color:#b0c4de;}
```
CSS中，颜色值通常以以下方式定义:
* 十六进制 - 如：`#ff0000`
* RGB - 如：`rgb(255,0,0)`
* 颜色名称 - 如：`red`

### background-image

`background-image` 属性描述了元素的背景图像.

```
body {background-image:url('paper.gif');}
```

### background-repeat

默认情况下`background-image`属性会在页面的水平和垂直方向平铺。
可以设置只在水平方向平铺(reapeat-x)

```
body
{
background-image:url('gradient2.png');
background-repeat:repeat-x;
}
```
不平铺(no-repeat)

```
body
{
background-image:url('img_tree.png');
background-repeat:no-repeat;
}
```

### background-position

利用 `background-position` 属性改变图像在背景中的位置:

```
body
{
background-image:url('img_tree.png');
background-repeat:no-repeat;
background-position:right top;
}
```

### background-attachment

`background-attachment` 背景图像是否固定或者随着页面的其余部分滚动。

### 简写属性

背景颜色的简写属性为 "background":

```
body {background:#ffffff url('img_tree.png') no-repeat right top;}
```
当使用简写属性时，属性值的顺序为：

* background-color
* background-image
* background-repeat
* background-attachment
* background-position
以上属性无需全部使用，按照页面的实际需要使用。

## 实例

```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
<style>
body
{
	margin-left:200px;
	background:#5d9ab2 url('img_tree.png') no-repeat top left;
}

.container
{
	text-align:center;
}

.center_div
{
	border:1px solid gray;
	margin-left:auto;
	margin-right:auto;
	width:90%;
	background-color:#d0f0f6;
	text-align:left;
	padding:8px;
}
</style>
</head>

<body>
<div class="container">
<div class="center_div">
<h1>Hello World!</h1>
<p>This example contains some advanced CSS methods you may not have learned yet. But, we will explain these methods in a later chapter in the tutorial.</p>
</div>
</div>
</body>
</html>
```

