# promise
> Promise 的**含义**:是异步编程的一种解决方案,简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果
> Promise对象特点：</br>
> 　　1、对象的状态不受外界影响。Promise对象代表一个异步操作，有三种状态：Pending（进行中）、Resolved（已完成，又称 Fulfilled）和Rejected（已失败）。</br>
> 　　2、一旦状态改变，就不会再变，任何时候都可以得到这个结果。Promise对象的状态改变，只有两种可能：从Pending变为Resolved和从Pending变为Rejected。

----------

####1、基本用法：

    var promise = new Promise(function(resolve, reject) {
      if (/* 异步操作成功 */){
    	resolve(value);
      } else {
      	reject(error);
      }
    });
Promise构造函数接受一个函数作为参数，该函数的两个参数分别是resolve和reject。它们是两个函数，由JavaScript引擎提供，不用自己部署。</br>
1、resolve:从“未完成”变为“成功”,在异步操作成功时调用，并将异步操作的结果，作为参数传递出去<br>
2、reject：从“未完成”变为“失败”，在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。<br>
3、Promise实例生成以后，可以用then方法分别指定Resolved状态和Reject状态的回调函数。<br>

    promise.then(function(value) {
      // success
    }, function(error) {
      // failure
    });

----------
下面是一个用Promise对象实现的Ajax操作的例子

    var getJSON = function(url) {
      var promise = new Promise(function(resolve, reject){
    var client = new XMLHttpRequest();
    client.open("GET", url);
    client.onreadystatechange = handler;
    client.responseType = "json";
    client.setRequestHeader("Accept", "application/json");
    client.send();
    
    function handler() {
      if (this.readyState !== 4) {
    return;
      }
      if (this.status === 200) {
    resolve(this.response);
      } else {
    reject(new Error(this.statusText));
      }
    };
      });
    
      return promise;
    };
    
    getJSON("/posts.json").then(function(json) {
      console.log('Contents: ' + json);
    }, function(error) {
      console.error('出错了', error);
    });

----------
如果调用resolve函数和reject函数时带有参数，那么它们的参数会被传递给回调函数。reject函数的参数通常是Error对象的实例，表示抛出的错误；resolve函数的参数除了正常的值以外，还可能是另一个Promise实例，表示异步操作的结果有可能是一个值，也有可能是另一个异步操作，比如像下面这样。

    var p1 = new Promise(function (resolve, reject) {
      // ...
    });
    
    var p2 = new Promise(function (resolve, reject) {
      // ...
      resolve(p1);
    })
上面代码中，p1和p2都是Promise的实例，但是p2的resolve方法将p1作为参数，即一个异步操作的结果是返回另一个异步操作。

注意，这时p1的状态就会传递给p2，也就是说，p1的状态决定了p2的状态。如果p1的状态是Pending，那么p2的回调函数就会等待p1的状态改变；如果p1的状态已经是Resolved或者Rejected，那么p2的回调函数将会立刻执行。

    var p1 = new Promise(function (resolve, reject) {
      setTimeout(() => reject(new Error('fail')), 3000)
    })
    
    var p2 = new Promise(function (resolve, reject) {
      setTimeout(() => resolve(p1), 1000)
    })
    
    p2
      .then(result => console.log(result))
      .catch(error => console.log(error))
    // Error: fail

上面代码中，p1是一个Promise，3秒之后变为rejected。p2的状态在1秒之后改变，resolve方法返回的是p1。由于p2返回的是另一个 Promise，导致p2自己的状态无效了，由p1的状态决定p2的状态。所以，后面的then语句都变成针对后者（p1）。又过了2秒，p1变为rejected，导致触发catch方法指定的回调函数。

----------
