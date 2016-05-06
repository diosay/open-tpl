OTPL AST SPEC
==

### hh

# aa

## bb

### cc

#### dd


节点：
```js
interface Node{
    type:string,
    line:number,
    column:number,
    filename:string
}
```

块节点：
```js
interface Block : Node{
    type:'block',
    nodes:[Node]
}
```

单节点：
```js
interface Span : Node{
    type:'span'
}
```



条件节点：
```js

interface ExpressionNode : Span{
}

interface Conditional : Node{
    test : ExpressionNode,
    ifTrue:Node,    //获取当测试的计算结果为 false 时要执行的表达式。
    ifFalse:Node
    
}
```

IF-ELIF-ELSE:
```js



interface IF : Node{
    type:'if',
    consequent:[Conditional]
}

interface ELIF : Conditional{
}

interface ELSE : Conditional{
    test:TRUE
}

interface binary{
    left:Node,
    right:Node,
    method:exp
}

```
https://msdn.microsoft.com/zh-cn/library/system.linq.expressions(v=vs.110).aspx

<pre>

                    | if |
         exp                       right
         



</pre>

+  plus
-  div
*  
/
=  
!  not
== eq
!= ne
>  gt
>= ge
<  lt
<= le
??
?:
