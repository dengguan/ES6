### 函数参数
1. 函数其实是接受arguments对象来访问参数列表，即arguments[0]...
2. ```
function add(num1,num2){
    arguments[1]=10;
    alert(arguments[0]+num2)
}
add(1,2)
```
参数值和arguments数组的值同步，但是如果只传入一个参数则不影响
