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
