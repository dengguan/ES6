## callee和caller的作用
1. **callee**：指向拥有当前arguments对象的函数，详见下面的阶乘函数

        function factorial(num){
	      if(num<=1){
	    return 1;
	      }else {
	    return num * arguments.callee(num-1);
	      }
	    }
2. **caller**:保存着引用当前函数的函数的引用
