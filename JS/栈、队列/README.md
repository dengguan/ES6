## 引用类型
1. 检测数组：Array.isArray()参数是值
2. 栈、队列方法：
	* push()是将参数诸葛添加到数组末尾
	* shift()将数组第一项返回并移除数组元素和长度

			var number = Array("1","2","3","4");
		    number.push("5");
		    console.log(number);//1 2 3 4 5
		    console.log(number.pop());//5
		    console.log(number);//1 2 3 4
		
		    console.log(number.shift());//1
		    console.log(number.unshift("0"));//4 在数组前端添加项并返回长度
		    console.log(number);//0 2 3 4
	* 