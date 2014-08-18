Object 对象
========


在OTPL里是以弱类型表示对象，也就是理论上是不区分数据类型的。
解释器在执行时会根据表达式需要来进行转换，大体转换规则如下（以JAVA为例子）：
`数字` 分为小数和整数:
小数转换为 double
整数转换为 long




OTPL表达式

{object} 直接打印对象。这个对象可以是模板变量或编译时变量(上下文变量)。

{object | format='rule'} 将对象进行格式化并打印。

{object.pro} 打印对象的 prop 字段或属性(java 会优先查找以 get 开始的无参数方法)。

{object[index]} 打印对象的索引值，index 的值可以是整数或字符串这取决区集合(map)的索引类型。

注意在实现 OTPL 中要求尽可能不出现异常，所以如果对象不存在则返回 null 而不是提未对象不存在，如：
{foo.bar} foo对象不存在，则并不返回错误，面是返回 null 。
当然，这个功能应该是可设置的。

类型转换，所有类型：
整  数：int(object)
小  数：num(object)
日  期：time(object)
字符串：str(object,[object1,objectN])
迭  代：特殊类型
集  合：特殊类型
json字符串:json(object)*









