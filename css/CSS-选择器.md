## 简单选择器

### 类型选择器 ／标签选择器 ／元素选择器

```
<p>What color do you like?</p>

p {
  color: red;
}
```

### id 选择器
`id` 选择器可以为标有特定`id`的HTML元素制定特定的样式，只能用于一个元素。    
CSS中`id` 选择器以`#`来定义。以下的样式规则应用于元素属性 id="para1":

```
#para1
{
text-align:center;
color:red;
}
```

### class 选择器
class选择器用于描述一组元素的样式，class选择器可以在多个元素中使用。
CSS中`class` 选择器以`.`来定义。在以下的例子中，所有拥有 center 类的 HTML 元素均为居中。

```
.center {text-align:center;}
```
直接制定特定HTML元素使用class。

```
p.center {text-align:center;}
```

### 通用选择器（Universal selector）
通用选择器允许选择一个页面中的所有元素。在大型网页使用它对性能有明显的影响：网页显示比预期要慢，一般情况下不要使用它。
 
```
* {
  padding: 5px;
  border: 1px solid black;
  background: rgba(255,0,0,0.25)
}
```

### 组合器（Combinators）
在CSS中，组合器允许你将多个选择器组合在一起。有以下四种可用的类型：
* 后代选择器——`空格键`——允许您选择嵌套在另一个元素中的某个元素，不一定是直接的后代;例如，它可以是一个孙子）。
* 子选择器—— `>` ——允许您选择一个元素，该元素是另一个元素的直接子元素。
* 相邻兄弟选择器—— `+` ——允许您选择一个元素，它是另一个元素的直接兄弟元素(也就是说，在它的旁边，在层次结构的同一层)。
* 通用兄弟选择器—— `~` — —允许您选择其他元素的兄弟元素(例如，在层次结构中的相同级别，但不一定就在它的旁边)。

```
<section>
  <h2>Heading 1</h2>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
  <div>
    <h2>Heading 2</h2>
    <p>Paragraph 3</p>
    <p>Paragraph 4</p>
  </div>
</section>
```

```
/*选择section元素下所有的p元素，包括子元素和孙子元素*/
section p {
  color: blue;
}
/*选择section元素下的p元素，只包括子元素*/
section > p {
  background-color: yellow;
}
/*选择h2元素直接相连的p元素*/
h2 + p {
  text-transform: uppercase;
}
/*选择与h2元素相同级别的p元素*/
h2 ~ p {
  border: 1px dashed black;
}
```

## 属性选择器

属性选择器是一种特殊类型的选择器，根据元素的属性和属性值来匹配元素。通用语法由方括号[] 组成， 其中包含属性名称，后跟可选条件以匹配属性的值。属性选择器可以根据其匹配属性值的方式分为2类：
* 存在和值属性选择器
* 子串值属性选择器

### 存在和值属性选择器

这些属性选择器尝试匹配精确的属性址：
* [attr]: 该选择器选择包含attr属性的所有元素，不论 attr 的值为何
* [attr=val]: 该选择器仅选择attr属性被赋值为val的所有元素
* [attr~=val]: 该选择器仅选择attr属性的值中有包含 val 值的所有元素

```
我的食谱配料: <i lang="fr-FR">Poulet basquaise</i>
<ul>
  <li data-quantity="1kg" data-vegetable>Tomatoes</li>
  <li data-quantity="3" data-vegetable>Onions</li>
  <li data-quantity="3" data-vegetable>Garlic</li>
  <li data-quantity="700g" data-vegetable="not spicy like chili">Red pepper</li>
  <li data-quantity="2kg" data-meat>Chicken</li>
  <li data-quantity="optional 150g" data-meat>Bacon bits</li>
  <li data-quantity="optional 10ml" data-vegetable="liquid">Olive oil</li>
  <li data-quantity="25cl" data-vegetable="liquid">White wine</li>
</ul>
```
```
/* 
    具有"data-vegetable"属性的所有元素,
    将被给予绿色的文本颜色
*/
[data-vegetable] {
  color: green
}

/* 
    具有"data-vegetable"属性且属性值刚好是"liquid"的所有元素，
    将被给予金色背景颜色 
*/
[data-vegetable="liquid"] {
  background-color: goldenrod;
}

/* 
    具有"data-vegetable"属性且属性值包含"spicy"的所有元素，
    即使某元素的该属性还包含其他属性值，
    都会被给予红色的文本颜色 
*/
[data-vegetable~="spicy"] {
  color: red;
}
```

### 子串值属性选择器

这种情况的属性选择器也被称为“伪正则选择器”，因为它们提供类似 regular expression 的灵活匹配方式，（但请注意，这些选择器并不是真正的正则表达式）：

* [attr|=val] : 选择attr属性的值以val（包括val）或val-开头的元素（-用来处理语言编码）。
* [attr^=val] : 选择attr属性的值以val开头（包括val）的元素。
* [attr$=val] : 选择attr属性的值以val结尾（包括val）的元素。
* [attr*=val] : 选择attr属性的值中包含字符串val的元素。

```
我的食谱配料: <i lang="fr-FR">Poulet basquaise</i>
<ul>
  <li data-quantity="1kg" data-vegetable>Tomatoes</li>
  <li data-quantity="3" data-vegetable>Onions</li>
  <li data-quantity="3" data-vegetable>Garlic</li>
  <li data-quantity="700g" data-vegetable="not spicy like chili">Red pepper</li>
  <li data-quantity="2kg" data-meat>Chicken</li>
  <li data-quantity="optional 150g" data-meat>Bacon bits</li>
  <li data-quantity="optional 10ml" data-vegetable="liquid">Olive oil</li>
  <li data-quantity="25cl" data-vegetable="liquid">White wine</li>
</ul>
```
```
/* 语言选择的经典用法 */
[lang|=fr] {
  font-weight: bold;
}

/* 
    具有"data-vegetable"属性含有值"not spicy"的所有元素,都变回绿色
*/
[data-vegetable*="not spicy"] {
  color: green;
}

/* 
   具有"data-quantity"属性其值以"kg"结尾的所有元素*/
[data-quantity$="kg"] {
  font-weight: bold;
}

/* 
   具有属性"data-quantity"其值以"optional"开头的所有元素 
*/
[data-quantity^="optional"] {
  opacity: 0.5;
}
```

## 伪选择器
不选择实际元素，而是元素的某些部分，或仅在某些上下文中的元素。

### 伪类
一个CSS伪类是一个以冒号(`:`)作为前缀的关键字，当你希望样式在特定的状态下才被呈现到指定的元素时，你可以往元素的选择器后面加上对应的伪类。

```
<a href="https://developer.mozilla.org/" target="_blank">Mozilla Developer Network</a>
```
```
/* These styles will style our link
   in all states */
a {
  color: blue;
  font-weight: bold;
}

/* We want visited links to be the same color
   as non visited links */
a:visited {
  color: blue;
}

/* We highlight the link when it is
   hovered (mouse), activated
   or focused (keyboard) */
a:hover,
a:active,
a:focus {
  color: darkred;
  text-decoration: none;
}
```
### 伪元素

伪元素和伪类很像，同样是添加到选择器后面达到指定某个元素的某个部分,但是伪元素前缀是两个冒号（`::`）
* `::after`
* `::before`
* `::first-letter`
* `::first-line`
* `::selection`
* `::backdrop`

```
<ul>
  <li><a href="https://developer.mozilla.org/en-US/docs/Glossary/CSS">CSS</a> defined in the MDN glossary.</li>
  <li><a href="https://developer.mozilla.org/en-US/docs/Glossary/HTML">HTML</a> defined in the MDN glossary.</li>
</ul>
```
```
/* All elements with an attribute "href", which values
   start with "http", will be added an arrow after its
   content (to indicate it's an external link) */
[href^=http]::after {
  content: '⤴';
}
```

## 组合器和多个选择器

### 组合器
一次使用一个选择器是很有用的，但在某些情况下却可能效率低下。将它们组合在一起，可以使 CSS选择器变得更加有用。

| Combinators | 详解 |
| :-- | :-- | 
|A,B | 匹配满足A（和/或）B的任意元素 |
|A B | 匹配任意元素，满足条件：B是A的后代结点（B是A的子节点，或者A的子节点的子节点） | 
|A > B | 匹配任意元素，满足条件：B是A的直接子节点 | 
|A + B | 匹配任意元素，满足条件：B是A的下一个兄弟节点（AB有相同的父结点，并且B紧跟在A的后面） | 
|A ~ B | 匹配任意元素，满足条件：B是A之后的兄弟节点中的任意一个（AB有相同的父节点，B在A之后，但不一定是紧挨着A） |  

```
<table lang="en-US" class="with-currency">
  <thead>
    <tr>
      <th scope="col">Product</th>
      <th scope="col">Qty.</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <th colspan="2" scope="row">Total:</th>
      <td>148.55</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Lawnchair</td>
      <td>1</td>
      <td>137.00</td>
    </tr>
    <tr>
      <td>Marshmallow rice bar</td>
      <td>2</td>
      <td>1.10</td>
    </tr>
    <tr>
      <td>Book</td>
      <td>1</td>
      <td>10.45</td>
    </tr>
  </tbody>
</table>
```

```
/* table元素 */
table {
  font: 1em sans-serif;
  border-collapse: collapse;
  border-spacing: 0;
}

/* table 元素中的所有 td，th 元素*/
table td, table th {
  border : 1px solid black;
  padding: 0.5em 0.5em 0.4em;
}

/* table 元素下的 thead 元素下的 th元素*/
table thead th {
  color: white;
  background: black;
}

/* All <td>s preceded by another <td>,
   within a <tbody>, within a <table> */
table tbody td + td {
  text-align: center;
}

/* All <td>s that are a last child,
   within a <tbody>, within a <table> */
table tbody td:last-child {
  text-align: right
}

/* All <th>s, within a <tfoot>s, within a <table> */
table tfoot th {
  text-align: right;
  border-top-width: 5px;
  border-left: none;
  border-bottom: none;
}

/* All <td>s preceded by a <th>, within a <table> */
table th + td {
  text-align: right;
  border-top-width: 5px;
  color: white;
  background: black;
}

/* All pseudo-elements "before" <td>s that are a last child,
   appearing within elements with a class of "with-currency" that
   also have an attribute "lang" with the value "en-US" */
.with-currency[lang="en-US"] td:last-child::before {
  content: '$';
}

/* All pseudo-elements "after" <td>s that are a last child,
   appearing within elements with the class "with-currency" that
   also have an attribute "lang" with the value "fr" */
.with-currency[lang="fr"] td:last-child::after {
  content: ' €';
}
```

### 同一规则集上的多个选择器

书写多个选择器，为了让相同规则集一次性作用于多组被选择的元素，你可以用逗号来隔开

```
h1, h2, h3, h4, h5, h6 {
  font-family: helvetica, 'sans serif';
}
```

