当页面加载完成的时候，标签head里的内容，是不会在页面中呈现出来的。它包含了像页面的<title>(标题) ,引入CSS(如果你想用CSS来美化页面内容)，图标和其他的元数据(比如 作者，关键词，摘要)。
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="author" content="Chris Mills">
    <meta name="description" content="The MDN Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications.">
    <title>My test page</title>
  </head>
  <body>
    <p>This is my page</p>
  </body>
</html>
```
## 什么是Head标签 
head 标签是 `<head>` 元素的内容， head的内容不会在浏览器中显示，它包含了页面的元数据。

## 标题
`<title>` 给 html 文档添加标题 
```
<title>My test page</title>
```

## 元数据 <meta> 元素

### 指定字符编码
```
<meta charset="utf-8">
```
### 添加作者和描述
* name 特性指定了meta 元素的类型; 说明该元素包含了什么类型的信息。
* content 指定了实际的元数据内容。
```
<meta name="author" content="Chris Mills">
<meta name="description" content="The MDN Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications.">
```

## CSS
```
<link rel="stylesheet" href="my-css-file.css">
```
# JavaScript 
```
<script src="my-js-file.js"></script>
```