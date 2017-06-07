## prototype、call、apply、bind
1. prototype:保存所有引用类型的所有实例方法(toString、valueOf),但是他的属性不可枚举，不能用for-in

2. call、apply方法都是为了给函数设置不同的this(作用域)
	
	    window.color="red";
	    	var o ={color:"blue"};
	    function sayColor() {
	      alert(this.color);
	    }
	    sayColor();//red
	    sayColor.call(this);//red
	    sayColor.call(window);//red
	    sayColor.call(o);//blue

3.call、apply的区别：他们分别都接收2个参数(作用域，参数),call必须要逐个列举出来

4.bind:这个方法会创建一个函数的实例，this值会被绑定成传给bind的值