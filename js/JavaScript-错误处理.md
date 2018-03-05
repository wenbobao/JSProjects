# 异常处理
可以用 throw 语句抛出一个异常并且用 try...catch 语句捕获处理它。

## 异常类型
JavaScript 可以抛出任意对象。尽管抛出数值或者字母串作为错误信息十分常见，但是通常用下列其中一种异常类型来创建目标更为高效：
* ECMAScript exceptions
* DOMException
* nsIXPCException (XPConnect)

## 抛出语句
```
throw "Error2";   // String type
throw 42;         // Number type
throw true;       // Boolean type
throw {toString: function() { return "I'm an object!"; } };
```

## try...catch 语句
```
openMyFile();
try {
    writeMyFile(theData); //This may throw a error
}catch(e){
    handleError(e); // If we got a error we handle it
}finally {
    closeMyFile(); // always close the resource
}
```

