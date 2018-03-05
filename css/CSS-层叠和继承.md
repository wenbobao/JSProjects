## 层叠
### 重要性
在CSS中，有一个特别的语法可以让一条规则总是优先于其他规则：`!important`。把它加在属性值的后面可以使这条声明有无比强大的力量。  

```
<p class="better">This is a paragraph.</p>
<p class="better" id="winning">One selector to rule them all!</p>
```
```
#winning {
  background-color: red;
  border: 1px solid black;
}

.better {
  background-color: gray;
  border: none !important;
}

p {
  background-color: blue;
  color: white;
  padding: 5px;
}
```

知道 `!important`存在是很有用的，这样当你在别人的代码中遇到它时，你就知道它是什么了。但是！我们建议你千万不要使用它，除非你绝对必须使用它。您可能不得不使用它的一种情况是，当您在CMS中工作时，您不能编辑核心的CSS模块，并且您确实想要重写一种不能以其他方式覆盖的样式。 但是，如果你能避免的话，不要使用它。由于 !important 改变了层叠正常工作的方式，因此调试CSS问题，尤其是在大型样式表中，会变得非常困难。
