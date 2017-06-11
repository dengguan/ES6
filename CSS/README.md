## 面试
* 
> 行内元素：a、b、span、img、input、strong、select、label、em、button、textarea

> 块级元素：div、ul、li、dl、dt、dd、p、h1-h6、blockquote

> 空元素：即系没有内容的HTML元素，例如：br、meta、hr、link、input、img

* **页面导入样式时，使用link和@import有什么区别？**

  （1）link属于XHTML标签，除了加载CSS外，还能用于定义RSS, 定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;

  （2）页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;

  （3）import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题;

* **介绍一下你对浏览器内核的理解？**

  主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。
  渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。

  JS引擎则：解析和执行javascript来实现网页的动态效果。

  最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。

* **常见的浏览器内核有哪些？**

  Trident内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称MSHTML]

  Gecko内核：Netscape6及以上版本，FF,MozillaSuite/SeaMonkey等

  Presto内核：Opera7及以上。      [Opera内核原为：Presto，现为：Blink;]

  Webkit内核：Safari,Chrome等。   [ Chrome的：Blink（WebKit的分支）]

* **常见状态码：**

100-199 用于指定客户端应相应的某些动作。 

200-299 用于表示请求成功。 

300-399 用于已经移动的文件并且常被包含在定位头信息中指定新的地址信息。
 
400-499 用于指出客户端的错误。 

500-599 用于支持服务器错误。

* **XHR**

	    var xhr = new XMLHttpRequest();
	    xhr.onreadystatechange = function () {
	      if (xhr.readyState==4) {
	    console.log(xhr.responseText);
	      }
	    };
	    xhr.open("get","http://wthrcdn.etouch.cn/weather_mini?city=北京",true);
	    xhr.send(null);

xhr.timeout=1000;

xhr.ontimeout=function(){}//超过1秒会调用方法

* **get、post区别：**

GET - 从指定的资源请求数据。有长度限制
POST - 向指定的资源提交要被处理的数据。没长度限制，参数不会显示在URL中