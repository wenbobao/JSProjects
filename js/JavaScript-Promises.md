从 ECMAScript 6 开始，JavaScript 增加了对 Promise 对象的支持，它允许你对延时和异步操作流进行控制。 
Promise 对象有以下几种状态: 
* pending (进行中): 初始的状态，即正在执行，不处于 fulfilled 或 rejected 状态。
* fulfilled (已完成): 成功的完成了操作。
* rejected (已失败): 失败，没有完成操作。
* settled (已解决): Promise 处于 fulfilled 或 rejected 二者中的任意一个状态, 不会是 pending。

![](https://mdn.mozillademos.org/files/8633/promises.png)

下面是一个简单的http网络请求的例子：

```
function imgLoad(url) {
  return new Promise(function(resolve, reject) {
    var request = new XMLHttpRequest();
    request.open('GET', url);
    request.responseType = 'blob';
    request.onload = function() {
      if (request.status === 200) {
        resolve(request.response);
      } else {
        reject(Error('Image didn\'t load successfully; error code:' 
                     + request.statusText));
      }
    };
    request.onerror = function() {
      reject(Error('There was a network error.'));
    };
    request.send();
  });
}
```