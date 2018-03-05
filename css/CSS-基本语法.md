## CSS 语法简介

### CSS 规则
CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明:
![](http://www.runoob.com/images/selector.gif)
1. 选择器: 需要修改样式的HTML元素
2. 属性: 设置的样式属性

### CSS 实例
CSS声明总是以分号`;`结束，声明组以大括号`{}`扩起来。

```
p
{
color:red;
text-align:center;
}
```

### CSS 注释
CSS注释以 `/*` 开始, 以 `*/` 结束, 实例如下:

```
/*这是个注释*/
p
{
text-align:center;
/*这是另一个注释*/
color:black;
font-family:arial;
}
``` 
## 引入样式表

### 外部样式表(External style sheet)

当样式需要应用于很多页面时，外部样式表将是理想的选择。

```
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```
```
hr {color:sienna;}
p {margin-left:20px;}
body {background-image:url("/images/back40.gif");}
```

### 内部样式表

当单个文档需要特殊的样式时，就应该使用内部样式表。使用 <style> 标签在文档头部定义内部样式表,如下：

```
<head>
<style>
hr {color:sienna;}
p {margin-left:20px;}
body {background-image:url("images/back40.gif");}
</style>
</head>
```

### 内联样式
由于要将表现和内容混杂在一起，内联样式会损失掉样式表的许多优势。请慎用这种方法，例如当样式仅需要在一个元素上应用一次时。    
要使用内联样式，你需要在相关的标签内使用样式（style）属性。Style 属性可以包含任何 CSS 属性。本例展示如何改变段落的颜色和左外边距：

```
<p style="color:sienna;margin-left:20px">这是一个段落。</p>
```

### 多重样式
如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从更具体的样式表中被继承过来。 

### 多重样式优先级

内联样式）Inline style > （内部样式）Internal style sheet >（外部样式）External style sheet > 浏览器默认样式

