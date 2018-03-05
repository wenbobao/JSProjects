盒模型是网页布局的基础--每个元素被表示为一个矩形的盒子，盒子的内容、内边距、边框和外边距像洋葱的膜那样，一层包着一层构建起来。

## 盒子属性

![](https://mdn.mozillademos.org/files/13647/box-model-standard-small.png)

* `width`和`height`: 设置内容盒（content box）的宽度和高度。内容盒是盒子内容显示的区域——包括盒子内的文本内容，以及表示嵌套子元素的其它盒子。还有其他属性可以更巧妙地处理内容的大小 — 设置大小约束而不是绝对的大小。这些属性包括min-width、max-width、min-height 和 max-height。
* `padding`: 表示一个CSS盒子的内边距，这一层位于内容盒的外边缘与边框的内边缘之间。该层的大小可以通过简写属性`padding`一次设置所有四个边，或用 `padding-top`、`padding-right`、`padding-bottom` 和 `padding-left` 属性一次设置一个边。
* `border`: CSS 盒的边框（border）是一个分隔层，位于内边距的外边缘以及外边距的内边缘之间。边框的默认大小为0。 `border` 简写属性可以让我们一次设置所有四个边，例如  `border: 1px solid black`; 但这个简写可以被各种普通书写的更详细的属性所覆盖：
1. border-top, border-right, border-bottom, border-left: 分别设置某一边的边框厚度／风格／颜色。
2. border-width, border-style, border-color: 分别仅设置边框的厚度／风格／颜色，并应用到全部四边边框。
3. 你也可以单独设置某一个边的三个不同属性，如 border-top-width, border-top-style, border-top-color，等
* `margin`: 外边距（margin）代表 CSS 盒子周围的外部区域，在布局中推开其它 CSS 盒子。其表现与与 padding 很相似；简写属性为 `margin`，单个属性分别为 `margin-top`、`margin-right`、`margin-bottom` 和 `margin-left`。

##  两种盒子模型

css中存在两种不同的盒子模型，可以通过box-sizing设置不同的模型。两种盒子模型，主要是width的宽度不同。

 * 标准盒子模型，width的长度等于content的宽度；
 * 将box-sizing的属性值设置成border-box时，盒子模型的width=border+padding+content的总和。


## 高级的盒子操作

### Overflow
当你使用绝对的值设置了一个盒子的大小，允许的大小可能不适合放置内容，这种情况下内容会从盒子溢出。我们使用`overflow`属性来控制这种情况的发生。

* `auto`: 当内容过多，溢出的内容被隐藏，然后出现滚动条来让我们滚动查看所有的内容。
* `hidden`: 当内容过多，溢出的内容被隐藏。
* `visible`: 当内容过多，溢出的内容被显示在盒子的外边（这个是默认的行为）

```
<p class="autoscroll">
   Lorem ipsum dolor sit amet, consectetur adipiscing elit.
   Mauris tempus turpis id ante mollis dignissim. Nam sed
   dolor non tortor lacinia lobortis id dapibus nunc. Praesent
   iaculis tincidunt augue. Integer efficitur sem eget risus
   cursus, ornare venenatis augue hendrerit. Praesent non elit
   metus. Morbi vel sodales ligula.
</p>

<p class="clipped">
   Lorem ipsum dolor sit amet, consectetur adipiscing elit.
   Mauris tempus turpis id ante mollis dignissim. Nam sed
   dolor non tortor lacinia lobortis id dapibus nunc. Praesent
   iaculis tincidunt augue. Integer efficitur sem eget risus
   cursus, ornare venenatis augue hendrerit. Praesent non elit
   metus. Morbi vel sodales ligula.
</p>

<p class="default">
   Lorem ipsum dolor sit amet, consectetur adipiscing elit.
   Mauris tempus turpis id ante mollis dignissim. Nam sed
   dolor non tortor lacinia lobortis id dapibus nunc. Praesent
   iaculis tincidunt augue. Integer efficitur sem eget risus
   cursus, ornare venenatis augue hendrerit. Praesent non elit
   metus. Morbi vel sodales ligula.
</p>
```
```
p {
  width  : 400px;
  height : 2.5em;
  padding: 1em 1em 1em 1em;
  border : 1px solid black;
}

.autoscroll { overflow: auto;    }
.clipped    { overflow: hidden;  }
.default    { overflow: visible; }
```
