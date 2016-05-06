# OTPL 模板语法


本文档是 OTPL 支持的语法功能的一个整体简介。

## 变量

变量会从当前模板的上下文上查找值，如果你想输出一个变量的值，可以使用：

```
{{ foobar }}
```

这样模板引擎将会从上下文上去查找变量 `foobar` 然后打印出来。变量可以使用 `.` 来访问属性，和 javascript([1]以下等同) 一样，也可以用 `[]`。

```
{{ foo.bar }}
{{ foo['bar'] }}
```

和 javascript 一样，这两种方式的结果都是一样的。

如果一个变量的值是 `null`，什么也不会被输出。同样的，如果引用了 `null` 的属性，也不会输出任何值（也不会报错）。下面的这些操作当 `foo == null` 的时候，都不会输出任何值：`{{ foo }}`, `{{ foo.bar }}`, `{{ foo.bar.baz }}`。

## 支持的数据类型

OTPL 支持的数据类型为：

- `Boolean` 布尔类型
	- true 真
	- false 假
- `Number` 数值类型(目前没有考虑到平台差异性如JS的整数和JAVA的整数的差异)
	- integer 整数, -2,147,483,648 到 2,147,483,647
    - *long 长整数，-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807
	- float 32 位浮点数，-3.4 × 1038 到 +3.4 × 1038，7 位
    - *double  64 位浮点数,±5.0 × 10−324 到 ±1.7 × 10308,15 到 16 位
- `String` 字符串
- `null` 空
- `Object` 对象
- `Array`/ `Map` [未实现]

`注：`数值类型目前精度未最终确认，OTPL致力于打造全平台通用所以必须找出一个折中的方案。

## 输出

使用 `{{ foo }}` 来打印 `escape` 之后的数据, `{{! foo }}}` 来输出 `unescape` 的原始数据。

```html
escaped: {{ foo }} 
unescaped: {{! foo }}
```

使用数据 `{ foo: "<script>" }` 渲染这个模板，将会得到下面的结果：

```html
escaped: &lt;script&gt;
unescaped: <script>
```

如果你希望输出最原始的数据（包括 `{{}}`），你需要使用 `{{%}}` 语法：

```html
{{%}}

{{x}}

{{%}}
```

渲染这个模板，将会得到下面的结果：

```
{{x}}
```

`注：` 在某些OTPL引擎实现中可能会对模板进行优化如：对空白行进行删除。只有在如:
```
{{'strings...'}}
```
的字符串是严格按模板输出的。

## 注释
OTPL 使用的与 `C/C++` 相同的注释方法。

`{{// comment }}` 为单个标签的注释，注意`不是`单行注释。

多行注释
```
{{/*}}
comments
{{*/}}
```
注释不会有任何输出。

## 作用域

OTPL采用的是单次渲染一个全局作用域，子模板与父模板使用同一个上下文，但有一个特殊的作用域那就是`块`调用
（参见块）。

parent.otpl:

```
{{ set a=1 }}
{{ set b = 2 }}
{{include "sub.otpl" }}
in parent:
a = {{ a }}
b = {{ b }}
{{#cblock b=2}}
```

sub.otpl:

```
in sub:
{{ set b = 3 }}
a = {{ a }}
b = {{ b }}

{{block cblock}}
in block:
a = {{ a }}
b = {{ b }}
{{/block}}
```

渲染 `parent.otpl`，将会得到下面的结果：

```
in sub:
a: 1
b: 3
in parent:
a: 1
b: 3
in block:
a: 1
b: 2
```


## 运算符
OTPL 支持在数据上使用一些操作符：

### 操作
- 加: `+`
- 减: `-`
- 乘: `*`
- 除: `/`
- 余: `%`

### 比较

- 等于：`==`
- 不等于：`!=`
- 大于：`>`
- 大于等于：`>=`
- 小于：`<`
- 小于等于:`<=`

### 逻辑运算
- 或运算：`||`
- 与运算：`&&`
- 非运算：`!`
- 空值运算： `??` {{值达式1 ?? 值达式2}}
- 三目运算： `?:` {{布尔表达式 ? 值表达式1 : 值表达式2}}


## 函数调用

你可以使用变量上提供的方法：

```js
var x = {
    hello:function(name){
        return 'hello '+name;
    }
};
```

```
{{x.hello('otpl!')}} //-> hello otpl!
```

`注：虽然OTPL支持这样的操作，但为了你的模板更加通用和效率更高，我们不推荐这样使用，应该使用一些内置方法来迭代这样的函数调用。`


### 内置函数

#### range(start, end[, step])/range(end)

如果需要迭代一些固定的数字，`range` 可以很方便的生成一个数字集合给你。这些数字从 `start` 开始，
然后按照 `step` (默认为1) 的数量进行递增或者递减，直到数字到达了 `stop`（不会包括 `stop`）。

```
{{for i:range(3)}}{{i}}{{/for}}
{{for i:range(1,3)}}{{i}}{{/for}}
{{for i:range(1,3,-1)}}{{i}}{{/for}}
```

渲染这个模板，将会得到结果：

```
012
12
321
```

#### now()
获取当前时间戳[x]

#### int(value)
将一个值转换为整数

#### float(value)
将一个值转换浮点数

#### str(value[,...])
将给定参数转换为字符串并连接（如果多个参数）

#### len(value)
获取指定值的元素个数，如数组/MAP的长度、字符串字符数。
如果不可用则返回 `-1`。

### 内置过滤器

#### time(format)
格式化日期,格式如下：
- yyyy
- mm
- d
...

#### num(format)
格式化数字

#### c


## 命令

命令是一些特殊的区块，对于这些特殊的区块，OTPL 会做特殊的处理。
OTPL 自带了一些内置的命令，你也可以自己定义一些自己的命令。

### set

`set` 让你定义或者修改一个变量。

```
{{set x=1}}
{{set y=2}}
{{x}}
{{y+x}}
```
渲染这个模板，将会得到结果：

```
1
3
```


### if

`if` 检查一个条件，让你可以选择性的输出内容，它和大多编程语言中的 `if` 完全一致。

```
{{ if (variable) }}
    It is true
{{/if }}
```

如果 `variable` 定义了且值为 true, 将会输出 `It is true`，否则什么都不会输出。

同样，可以通过 `elif` 和 `else` 增加判断中的其他条件：

```
{{ if (hungry) }}
    I am hungry
{{ elif (tired) }}
    I am tired
{{ else }}
    I am good!
{{/if }}
```

### for

`for` 可以对 arrays 和 dictionaries 进行迭代：

```js
{{ set array = ['foo','bar'] }}
{{ set map = {'foo':'bar'} }}

{{for index : array}}
    {{index}} {{array[index]}}
{{/for}}

{{for key,value : map}}
    {{key}} {{value}}
{{/for}}

{{for item : map}}
    {{item.key}} {{item.value}}
{{/for}}


{{ for i : range(2)}}
    {{i}}
{{/for}}

```

渲染这个模版，将会得到结果：

```
0 foo
1 bar

foo bar
foo bar

0
1
```

### 块

块允许你定义一个可复用的代码片段和位置预留，下面是一个例子：

```
{{block test}}
    param is {{param}}
{{/block}}
```

调用块:

```
{{#test 'test',param=2 )}}

```

渲染结果是：

```
param is 2
```

注意: 在块中，你不能改变外层作用域上的任何变量，但是仍然可以使用它们。

### include

include 引入其他的模板。它在你想要共享不同的小的区块时非常有用。

```
{{ include "item.html" }}
```

## layout

layout 你更容易的来复用模板。当编写一个模板的时候，你可以调用 `块`，这样在子模板中可以实现这些块。


layout.otpl

```html
<!doctype html>
<html>
    <head>
        <meta name="charset" content="utf-8" />
        <title>{{title}}</title>
        {{#head}}
    </head>
    <body>
        {{body}}
    </body>
</html>
```

item.otpl

```html
{{layout 'layout.otpl'}}

{{block head}}
    <link type="text/css" href="test.css" rev="stylesheet" rel="stylesheet"/>
{{/block}}

<h2>Hello {{title}}</h2>
```

然后我们使用数据 `{title: 'OTPL'}` 渲染 `item.otpl`，将会得到下面的结果：

```html
<!doctype html>
<html>
    <head>
        <meta name="charset" content="utf-8" />
        <title>OTPL</title>
        <link type="text/css" href="test.css" rev="stylesheet" rel="stylesheet"/>
    </head>
    <body>
        <h2>Hello OTPL</h2>
    </body>
</html>
```

## 保留关键词

- `debugger`
- `exit`
- `extend`
- `layout`
- `import`
- `include`
- `block`
- `macro`
- `parse`
- `range`
- `set`
- `with`
- `void`
- `true`
- `false`
- `null`
- `each`
- `if`
- `elif`
- `else`
- `for`
- `in`



## 说明

[1]: javascript 只是本文档一种描述举例，OTPL是平台无关的，也就是说完全可以工作在 JAVA/C#、PHP/Python 等为代表的静/动态类型语言。
