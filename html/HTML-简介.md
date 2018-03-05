## html 简介
HTML (HyperText Markup Language) 不是一种编程语言;它是一种标记语言，用于告诉您的浏览器如何构造您访问的网页。
HTML 由一系列的元素(elements)组成。下面是一个完整的HTML页面： 
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <p>This is my page</p>
  </body>
</html>
```
## html 元素
HTML 元素指的是从开始标签（start tag）到结束标签（end tag）的所有代码。

![](https://mdn.mozillademos.org/files/9347/grumpy-cat-small.png)

我们的元素的主要部分是：

1. 开始标签（Opening tag）：这包括元素的名称（在这种情况下，p），包裹在开始和结束尖括号中。这表示元素开始或开始生效 - 在这种情况下，表示了一个段落的开头。
1. 结束标记（Closing tag）：这与开始标记相同，除了它在元素名称之前包含正斜杠。这表示元素结束的位置 - 在这种情况下，表示了一个段落的结尾. 没有包含结束标记是一个常见的初学者错误，并可能导致奇怪的结果。
1. 内容（Content）：这是元素的内容，在这种情况下只是文本。
1. 元素（Element）：开始标记，加上结束标记，加上内容，等于元素。

### 嵌套元素
可以把元素放到其它元素之中——这被称作嵌套。 
```
<p>My cat is <strong>very</strong> grumpy.</p>
```
### 块级元素和内联元素

* 块级元素在页面中以块的形式展现 —— 相对与其前面的内容它会出现在新的一行，其后的内容也会被挤到下一行展现。块级元素通常用于展示页面上结构化的内容，类似于段落、列表、导航菜单、页脚等等。一个以block形式展现的块级元素不会被嵌套进内联元素中，但可以嵌套在其它块级元素中。
* 内联元素通常出现在块级元素中并被一些其它文本所包围，而不是一整个段落或者一组内容。内联元素不会导致文本换行：它通常出现在一堆文字之间例如超链接元素<a>或者强调元素<em>和 <strong>。
例如： 
```
<em>first</em><em>second</em><em>third</em>

<p>fourth</p><p>fifth</p><p>sixth</p>
```
### 空元素
不是所有元素都拥有开始标签，内容和结束标记. 一些元素只有一个标签。 
```
<img src="https://raw.githubusercontent.com/mdn/beginner-html-site/gh-pages/images/firefox-icon.png">
```
## 属性
HTML 元素可以拥有属性。属性提供了有关 HTML 元素的更多的信息。
属性总是以名称/值对的形式出现，比如：name="value"。
属性总是在 HTML 元素的开始标签中规定。
属性的值要加`""`
![](https://mdn.mozillademos.org/files/9345/grumpy-cat-attribute-small.png)

### 布尔属性
有时你会看到没有值的属性，它是合法的。这些属性被称为布尔属性，他们只能有跟它的属性名一样的属性值。 
```
<input type="text" disabled="disabled">
<input type="text" disabled>
```
## HTML中的空白
下面的两个例子是等价的。
```
<p>Dogs are silly.</p>

<p>Dogs        are
         silly.</p>
```
无论用了多少空格包括换行，当渲染这些代码的时候，HTML解释器会将连续出现的空白字符减少为一个单独的空格符。

## HTML注释
<!--和-->
```
<!-- <p>I am!</p> -->
```