### 变量
1. 操作5种基本类型时，因为他们是按值访问的，因此可以操作保存在变量中的实际值；但是操作对象时，因为不允许直接访问内存，所以实际上是操作的对象的引用(为对象添加属性时时操作的实际对象)
2. 复制变量时:基本类型是独立复制；变量是复制的值实际上是一个指针
3.     
		function setName(obj) {
	      obj.name = "Nicholas";
	      obj = new Object();
	      obj.name = "Greg";
	    }
	    var person = new Object();
	    setName(person);
	    alert(person.name); //"Nicholas"
在函数内部重写obj时，这个变量引用的是局部对象，函数执行完就会销毁
