循环提供了一种快速和简单的方式去做一些重复的事。JavaScript中提供了这些循环语句：
* for statement
* do...while statement
* while statement
* label statement
* break statement
* continue statement
* for...in statement
* for...of statement

## for 语句
一个for循环会一直重复执行，直到指定的循环条件为fasle

## do...while 语句
do...while 语句一直重复直到指定的条件求值得到假（false）。 
```
do {
   i += 1;
   document.write(i);
} while (i < 5);
```

## while 语句
一个 while 语句只要指定的条件求值为真（true）就会一直执行它的语句块。
```
n = 0;
x = 0;
while (n < 3) {
   n++;
   x += n;
}
```

## 标签语句
标签语句提供一种使你同一程序的在另一处找到它的标识。例如，你可以用一个标签来识别一个循环，并用break或continue语句来说明一个程序是否要中断这个循环或是继续执行。如下所示：markLoop这个标签定义了一个while循环。
```
markLoop:
while (theMark == true) {
   doSomething();
}
```

## 中断语句
使用中断语句终止循环、开关或与标签语句连接。
* 当你使用没有带标签语句的中断语句（break）时，while，do-while，for或者switch封闭的内部语句将立即终止，并转移到后面的语句执行。
* 当你使用带有标签语句的中断语句（break）时，将终止在特定的标签语句。
```
for (i = 0; i < a.length; i++) {
   if (a[i] == theValue)
      break;
}
```

```
var x = 0;
var z = 0
labelCancelLoops: while (true) {
    console.log("Outer loops: " + x);
    x += 1;
    z = 1;
    while (true) {
        console.log("Inner loops: " + z);
        z += 1;
        if (z === 10 && x === 10) {
            break labelCancelLoops;
        } else if (z === 10) {
            break;
        }
    }
}
```

## 连续语句
连续语句用于重新开始 while, do-while, for语句，或者标签语句（label statement）。

* 当你使用没有带标签语句的连续语句（continue Statement）时，将在当前的while，do-while或者for循环体封闭的内部语句中止执行，然后进入下一次循环继续执行。与中断语句（break Statement）相比，连续语句不会把整个循环终止。在while循环里，将跳回条件判断（condition）；在for循环里，则跳回累计表达式（increment-expression）。
* 当你使用带有标签语句的连续语句时，用于识别循环体中的标签语句。

```
i = 0;
n = 0;
while (i < 5) {
   i++;
   if (i == 3)
      continue;
   n += i;
}
```

```
checkiandj :
   while (i < 4) {
      document.write(i + "<br/>");
      i += 1;
      checkj :
         while (j > 4) {
            document.write(j + "<br/>");
            j -= 1;
            if ((j % 2) == 0)
               continue checkj;
            document.write(j + " is odd.<br/>");
         }
      document.write("i = " + i + "<br/>");
      document.write("j = " + j + "<br/>");
   }
```

## for...in 语句
for...in 语句迭代一个指定的变量去遍历这个对象的属性，每个属性，
```
for (variable in object) {
  statements
}
```

## for of 语句 
**该新特性属于 ECMAScript 2015（ES6）规范，在使用时请注意浏览器兼容性。**
for...of语句在可迭代的对象上创建了一个循环(包括Array, Map, Set, 参数对象（ arguments） 等等)，对值的每一个独特的属性调用一个将被执行的自定义的和语句挂钩的迭代。 
```
for (variable of object) {
  statement
}
```

下面的这个例子展示了 for...of 和 for...in 两种循环语句之间的区别。与 for...in 循环遍历的结果是数组元素的下标不同的是， for...of 遍历的结果是元素的值： 
```
let arr = [3, 5, 7];
arr.foo = "hello";

for (let i in arr) {
   console.log(i); // logs "0", "1", "2", "foo"
}

for (let i of arr) {
   console.log(i); // logs "3", "5", "7" // 注意这里没有 hello
}
```