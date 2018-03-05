# 注释
注释的语法与C++和许多其他语言中的语法相同：

```
// 单行注释
/* 这是一个更长的,
   多行注释
*/
/* 然而, 你不能, /* 嵌套注释 */ 语法错误 */
```
# 声明
JavaScript 有三种声明：
* `var` 声明一个变量
* `let` 声明一个块作用域的局部变量 (block scope local variable)
* `const` 声明一个只读的常量

# 变量

变量的命名（标识符）需要遵守一定的规则：
1. 必须以字母、下划线（_）、或者美元符号（$）开头
2. JavaScript 语言是区分大小写的

## 声明变量
1. 使用关键词 `var`, 例如： `var x = 42;` 这个语法可以用来声明局部变量和全局变量。
2. 直接赋值。 例如： `x = 42` 。这样就会声明了一个全局变量并会在严格模式下产生一个 ReferenceError。声明变量时不应该用这种方式。
3. 使用关键词 let。例如 `let y = 13`。这个语法可以用来声明块作用域的局部变量(block scope local variable)。

## 变量求值
使用`var` 或 `let` 声明的且没有设置值的变量，值会被设定为 `undefined `， 当试图访问一个未声明的变量或者访问一个使用 `let` 声明的且没有设置值的变量会导致一个 `ReferenceError ` 异常被抛出

```
var a;
// a 的值是 undefined
console.log("The value of a is " + a); 

// Uncaught ReferenceError: b is not defined
console.log("The value of b is " + b); 

// c 的值是 undefined 
console.log("The value of c is " + c); 
var c;

// Uncaught ReferenceError: x is not defined 
console.log("The value of x is " + x); 
let x;
```
因此可以使用 `undefined` 来判断变量是否已赋值。如下：

```
var input;
if(input === undefined){
  doThis();
} else {
  doThat();
}
```

注意：
1. `undefined` 值在布尔类型环境中 会被当作 false
2. `undefined` 值在数值环境中 会被转换为 `NaN`
3. `null` 值在布尔类型环境中 会被当作 false
4. `null` 值在数值环境中会被当作0来对待

## 变量的作用域
1. 全局变量： 在所有函数之外声明的变量
2. 局部变量： 在函数内部声明的变量
3. 在ES6 之前 JavaScript没有 `语句块` 作用域， 语句块中声明的变量将成为语句块所在代码段的局部变量，如下的代码将在控制台输出 5，因为 x 的作用域是声明了 x 的那个函数（或全局范围），而不是 if 语句块。 
```
if (true) {
  var x = 5;
}
console.log(x); // 5
```
4. 如果使用ES6 中的 `let`undefined` 声明,如下：   
```
if (true) {
  let y = 5;
}
console.log(y); // ReferenceError: y is not defined
```
## 变量声明提升

在Javascript中，你可以引用稍后声明的变量而不会引发异常。 不过在使用或引用这个提升后的变量将得到 undefined 值。  
```
console.log(x === undefined); // logs "true"
var x = 3;
```
因此 一个函数中所有的var 语句 应该尽量 放在函数的顶部。 
注意： 
在 ES6 中， let (const) 将不会提升变量 ，若提前引用这个变量，将抛出错误 `ReferenceError `。
```
console.log(x); // ReferenceError
let x = 3;
```
## 函数提升
对于函数，只有函数声明会被提升到顶部，而不包括函数表达式。
```
/* 函数声明 */

foo(); // "bar"

function foo() {
  console.log("bar");
}

/* 函数表达式   表达式定义的函数，称为匿名函数。匿名函数没有函数提升。*/

baz(); // TypeError: baz is not a function
//此时的"baz"相当于一个声明的变量，类型为undefined。
由于baz只是相当于一个变量，因此浏览器认为"baz()"不是一个函数。
var baz = function() {
  console.log("bar2");
};
```
## 全局变量
全局变量实际上是全局对象的属性。在网页中，全局对象是 window，所以你可以用形如 window.variable的语法来设置和访问全局变量。
## 常量
用关键字 `const` 创建一个只读的常量。 
常量不可以通过赋值改变其值，也不可以在脚本运行时重新声明。它必须被初始化为某个值。
常量的作用域规则与`let`块级作用域变量相同。若省略const关键字，则该标识符将被视为变量。
在同一作用域中，不能使用与变量名或函数名相同的名字来命名常量。
注意，对象属性是不受保护的： 
```
const MY_OBJECT = {"key": "value"};
MY_OBJECT.key = "otherValue";
```
