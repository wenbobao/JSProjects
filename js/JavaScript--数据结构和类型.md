## 数据类型
JavaScript语言可以识别下面7中不同类型的值：
1. 六种原型数据类型
* String 字符串
* Number 数字
* Boolean 布尔值 true & false
* null 一个表明 null 值的特殊关键字
* undefined 变量未定义时的属性。
* Symbol (在ES6 中新添加的类型)。一种数据类型，它的实例是唯一且不可改变的。

2. Object对象

## 数据类型的转换
JavaScript 是一种动态类型语言。这意味着你声明变量时可以不必指定数据类型，而数据类型会在脚本执行时根据需要自动转换。 
``` 
var answer = 42;
answer = "Hello";
```
在涉及加法运算符`+`的数字和字符串表达式中，JavaScript 会把数字值转换为字符串，如下： 
```
y = 42 + " is the answer" // "42 is the answer"
```
在涉及其他运算符，例如 `-`号， JavaScript语言不会把数字变为字符串，如下： 
```
"37" - 7 // 30
"37" + 7 // "377"
```
### 字符串转换为数字
以下方法可以将内存中的表示数字的字符串显示转化为对应的数字:
```
parseInt() 
parseFloat()
```
> 注意：
> 1. parseInt 仅能够返回整数，所以使用它会丢失小数部分。
> 2. parseInt 最好总是带上进制(radix) 参数，这个参数用于指定使用哪一种进制。

也可以使用单目加法运算符，将表示数字的字符串显示转化为数字 
```
"1.1" + "1.1" = "1.11.1"
(+"1.1") + (+"1.1") = 2.2   // 注：加入括号为清楚起见，不是必需的。
```

## 字面量
字面量是由语法表达式定义的常量，其值是固定的，而且在程序运行时不可更改。 常见的字面量如下：
* 数组字面量(Array literals)
* 布尔字面量(Boolean literals)
* 浮点数字面量(Floating-point literals)
* 整数(Intergers)
* 对象字面量(Object literals)
* RegExp literals
* 字符串字面量(String literals)

### 数组字面量

数组字面值是一个封装在方括号对 `[]`中的包含有零个或者多个表达式的列表，其中每个表达式代表数组的一个元素。当你使用数组字面值创建一个数组时，该数组将会以指定的值作为其元素进行初始化，而其长度被设定为元素的个数。

```
var coffees = ["French Roast", "Colombian", "Kona"];
var a=[3];
console.log(a.length); // 1
console.log(a[0]); // 3
```
当你用数组字面值组成数组时，连续写两个逗号，数组中就会产生一个没有被指定的元素，其初始值是undefined。
```
var fish = ["Lion", , "Angel"]; // 数组的长度为3 ，fish[0]是"Lion"，fish[1]是undefined，而fish[2]是"Angel"
```
如果在元素列表的尾部添加了一个逗号，他将会被忽略
```
var myList = ['home', , 'school', ]; // 数组的长度为3
var myList = [ , 'home', , 'school']; // 数组的长度为4
var myList = ['home', , 'school', , ]; // 数组的长度为4
```
**通过逗号，可以显式地将缺失的元素声明为undefined，将大大提高你的代码的清晰度和可维护性。**

### 布尔字面量 
布尔类型有两种字面量：`true`和`false`。

### 整数 
整数可以用十进制（基数为10）、十六进制（基数为16）、八进制（基数为8）以及二进制（基数为2）表示。
* 十进制整数字面量由一串数字序列组成，且没有前缀0。
* 八进制的整数以 0（或0O、0o）开头，只能包括数字0-7。
* 十六进制整数以0x（或0X）开头，可以包含数字（0-9）和字母 a~f 或 A~F。
* 二进制整数以0b（或0B）开头，只能包含数字0和1。
** 注意： 严格模式下，八进制整数字面量必须以0o或0O开头，而不能以0开头。** 
```
0, 117 and -345 (十进制, 基数为10)
015, 0001 and -0o77 (八进制, 基数为8) 
0x1123, 0x00111 and -0xF1A7 (十六进制, 基数为16或"hex")
0b11, 0b0011 and -0b11 (二进制, 基数为2)
```

### 浮点数字面量
浮点数字面值可以由以下的组成部分：
* 一个十进制整数，可以带正负号（即前缀“+”或“ - ”），
* 小数点（“.”），
* 小数部分（由一串十进制数表示），
* 指数部分
指数部分以“e”或“E”开头，后面跟着一个整数，可以有正负号（即前缀“+”或“-”）。浮点数字面量至少有一位数字，而且必须带小数点或者“e”（大写“E”也可）。
```
3.14      
-.2345789 // -0.23456789
-3.12e+12  // -3.12*1012
.1e-23    // 0.1*10-23=10-24=1e-24
```

### 对象字面量
对象字面值是封闭在花括号对({})中的一个对象的零个或多个"属性名-值"对的（元素）列表。可以使用数字或者字符串值作为属性的名字。
```
var car = {myCar: "hello"};
```

### RegExp 字面值
一个正则表达式是字符被斜线（译注：正斜杠“/”）围成的表达式。 
```
var re = /ab+c/;
```

### 字符串字面量
字符串字面量是由双引号（"）对或单引号（'）括起来的零个或多个字符。
```
"foo"
'bar'
"1234"
"one line \n another line"
"John's cat"
```

可以在字符串字面值上使用字符串对象的所有方法：
```
console.log("John's cat".length) 
// 将打印字符串中的字符个数（包括空格） 
// 结果为：10
```

1. 字符串插值 
```
var name = "Bob", time = "today";
`Hello ${name}, how are you ${time}?`
```
2. 多行字符串
```
// Multiline strings
`In JavaScript this is
 not legal.`
```
3. 除非有特别需要使用字符串对象，否则，你应当始终使用字符串字面值。
4. 在字符串中使用特殊字符
```
"one line \n another line"
```
以下表格列举了JavaScript的字符串中使用的特殊字符。
![](http://owik45kut.bkt.clouddn.com/QQ20170919-141759@2x.png)

5. 转义字符
通过在引号前加上反斜线'\'，可以在字符串中插入引号，这就是引号转义。
```
var quote = "He read \"The Cremation of Sam McGee\" by R.W. Service.";
console.log(quote);
// 代码的运行结果为:
He read "The Cremation of Sam McGee" by R.W. Service.
```

要在字符串中插入'\'字面值，必须转义反斜线。例如，要把文件路径 c:\temp 赋值给一个字符串，可以采用如下方式:
```
var home = "c:\\temp";
```
也可以在转行之前加上反斜线以转义换行，实际上就是一条语句拆成多行书写，这样反斜线和换行都不会出现在字符串的值中。
```
var str = "this string \
is broken \
across multiple\
lines."
console.log(str);   // this string is broken across multiplelines.
```
Javascript没有“heredoc”语法，但可以用行末的换行符转义和转义的换行来近似实现 
```
var poem = 
"Roses are red,\n\
Violets are blue.\n\
Sugar is sweet,\n\
and so is foo."
```
ECMAScript 2015 增加了一种新的字面量，叫做模板字面量 template literals。它包含一些新特征，包括了多行字符串！
```
var poem =
`Roses are red,
Violets are blue.
Sugar is sweet,
and so is foo.`
```