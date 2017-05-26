## 数据类型
1. 基本数据类型：
  * Undefined:声明了但是未初始化(有种情况就是声明也初始化了但是在调用的后面，那么会变量提升，但是赋值不提升)
  * Null:空对象指针
  * Bollean:注意不是1为true,0为false那么简单,其中Number()方法转换为Boolean值，注意数字任何非零值变成true，只有null对象、""空字符串才会转换成false
  * Number:0.1+0.2=0.300...4所以一定不要判断浮点数值的运算结果,其中有+-infinity正负无穷大，isFinite()函数判断在最大、小值之间返回true，Nan(not a number):他与任何值不相等，包括自己，isNaN()方法会将参数转换成数值，如果不能返回true
  * String
2. 复杂数据类型：
  * Object
3. typeOf操作符
  * 注意的是typeOf如果返回Object对应的值是对象或null
4. 数值转换:
  * Number():输入Undefined-Nan;输入null-0
  * parseInt():输入空-Nan;输入字符串会一直转换到第一个非数字字符
  * toString(进制):
  * String():null-"null",Undefined-"Undefined"
