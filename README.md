#OPEN TPL

**OTPL** (Open template programming language，开放模板编程语言) 它致力于实现一个跨平台跨语言的，
统一的，标准的，开放的模板编程语言。它非常的规范和工整：


```html
<html>
    <header>
        {{#header}}
    </header>
    <body>
        {{#body}}
    </body>
</html>
```


```html
{{layout "layout.otpl" }}

{{block header}}
<title>{{ title }}</title>
{{/block}}

<ul>
{{for name, item : items}}
  <li>{{ name }}: {{ item }}</li>
{{/for}}
</ul>
```

## 文档
[中文语法规范](https://github.com/diosay/open-tpl/blob/master/syntax-cn.md)

## 实现引擎

- [Nodejs](https://github.com/diosay/otpl-node) 
- Golang
- Java
- PHP
- C#/.Net 


##背景

模板语言从最早的ASP/PHP等混合语言发展到今天已经有众多优秀的模板语言如：
PHP的Smarty,JAVA的EL，.NET的Razor，Nodejs的Jade等等，但他们大多都在那一个领域里发展或对其语言进行补充，
这给前端同学（特别是供职过多家使用不同技术或语言的公司）来说增加了学习成本。同时项目带了很多低质量的代码。
不少模板语言非常的优雅如jade和razor 我非常喜欢这种风格，但是真正在项目中使用时特别是多人协作开发时写出的代码
就不那么的“优雅”或工程化了。这也是OTPL的产生的原因。

##许可协议
为了维护OTPL的统一性，OTPL使用对商业友好但不允许产生另一个“OTPL”的 知识共享署名-禁止演绎 4.0 国际许可协议进行许可。

[![cc-by-nd](https://i.creativecommons.org/l/by-nd/4.0/88x31.png)](http://creativecommons.org/licenses/by-nd/4.0/)






