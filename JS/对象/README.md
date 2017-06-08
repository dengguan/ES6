## 对象
1. 对象的特性是内部值:用2对方括号包起来，它描述了属性的特征
	
	- 数据属性：
		
	    - [[Configurable]]:表示能否删除从而重新定义属性
		- [[Enumerable]]:表示能否通过for-in循环返回属性
		- [[Writabel]]:能否修改属性的值
		- [[Value]]:属性的数据值
		- Object.defineProperty(对象,属性的名字,描述符对象)，还有一个definePropertys方法
		   
			    var person = {};
			    Object.defineProperty(person,"name",{
			      writable:false,
			      value:"bin"
			    });
			    alert(person.name);//bin
			    person.name="liu";
			    alert(person.name);//bin
	
	- 访问器属性：
		- [[Configurable]]:表示能否删除从而重新定义属性
		- [[Enumerable]]:表示能否通过for-in循环返回属性
		- [[Get]]:读取属性时调用的函数
		- [[Set]]:写入属性时调用的函数

2. 构造函数模式
	- 构造函数:
		1. 不创建对象
		2. 直接将属性方法赋给this对象
		3. 没有return语句
	- 构造函数每定义一个函数就实例化了一个对象，会导致不同作用域链和标识符解析

3. 原型模式
	- 可以让所有实例化的对象共享属性、方法

		    function person(){}
		    person.prototype.name="huangbin";
		    person.prototype.sayname = function() {
		      alert(this.name);
		    }
		    var person1 = new person();
		    person1.sayname();//huangbin
		    var person2 = new person();
		    alert(person1.sayname==person2.sayname)//true

4. [[Prototype]]指针指向**构造函数的原型对象**,在Firefox、Safari、Chrome中有**__proto__属性可以访问它**
5. Person.prototype.constructor指向Person

6. Person.prototype.isPrototypeOf(person1)是判断某个构造函数的原型对象是不是实例对象指向的
7. Object.getPrototypeOf():是返回实例对象的指向构造函数原型的指针([[Prototype]])

8. Person.hasOwnProperty("name")是判断属性是否来自实例
9. 要获取对象中可枚举的属性,可使用Object.keys()方法

10. 想要获得所有实例的属性，无论是否可枚举，Object.getOwnPropertyNames()
