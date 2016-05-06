#Opcode Defines

<table style="font-size:12px">
<tr>
<th>操作码</th>
<th>名称</th>
<th>符号</th>
<th>原形(指令结构)</th>
<th>长度</th>
</tr>

<tr>
<td rowspan=2>0</td>
<td>nop</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
表示一个占位，不执行任何操作。通常用作 label 使用。
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>doc</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{FILE_PATH_STR_LEN}{STR_BYTES}</td>
<td>9+N</td>
</tr><tr><td colspan=4>
表示一个文档，执行此操作时将打开该文档为执行。<br>
{FILE_PATH_STR_LEN}: 文件地址的字符串的字节长度。<br>
{STR_BYTES}:文件地址的字节组。
</td></tr>

<tr>
<td rowspan=2>2</td>
<td>prt</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出一个元素并打印到输出流。
</td></tr>

<tr>
<td rowspan=2>3</td>
<td>jmp</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{LINE}</td>
<td>13</td>
</tr><tr><td colspan=4>
无条件跳转到指定指令行。
</td></tr>

<tr>
<td rowspan=2>3</td>
<td>jmp_c</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{LINE}</td>
<td>13</td>
</tr><tr><td colspan=4>
从栈顶弹出一个元素，如果该对象为假(null,0,false)，则跳转到指定指令行。
</td></tr>

<tr>
<td rowspan=2>4</td>
<td>pop</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出一个元素，并丢弃。
</td></tr>


<tr>
<td rowspan=2>5</td>
<td>ldvar</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{INDEX_STR_LEN}{STR_BYTES}</td>
<td>13+N</td>
</tr><tr><td colspan=4>
根据给定索引，从变量组中获取一个对象，并将该对象压入栈顶。<br>
{INDEX_STR_LEN}: 索引名称的字符串的字节长度。<br>
{STR_BYTES}:索引的字节组。
</td></tr>

<tr>
<td rowspan=2>6</td>
<td>ldmem</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{ARGS_LEN}{INDEX_STR_LEN}{STR_BYTES}</td>
<td>17+N</td>
</tr><tr><td colspan=4>
从栈顶弹出一个对象O,并从中获取其成员对象(字段、属性、方法)，并将对象O与成员对象压入栈顶。<br>
{INDEX_STR_LEN}: 成员名称的字符串的字节长度。<br>
{STR_BYTES}:成员名称的字节组。<br>
{ARGS_LEN}: 参数长度。
</td></tr>


<tr>
<td rowspan=2>7</td>
<td>stvar</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{INDEX_STR_LEN}{STR_BYTES}</td>
<td>13</td>
</tr><tr><td colspan=4>
从栈顶弹出一个对象并将该对象设置到变量组中。<br>
{INDEX_STR_LEN}: 索引名称的字符串的字节长度。<br>
{STR_BYTES}:索引的字节组。
</td></tr>

<tr>
<td rowspan=2>8</td>
<td>call</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{ARGS_LEN}{METHOD_STR_LEN}{STR_BYTES}</td>
<td>17+N</td>
</tr><tr><td colspan=4>
从栈顶开始弹出执行方法所需对象并执行，将执行结果对象压入栈顶。<br>
弹出顺序为：<br>
对象实例；<br>
成员对象(方法)；<br>
参数(给定个数)。<br>
{METHOD_STR_LEN}: 方法名称的字符串的字节长度。<br>
{STR_BYTES}:索引的字节组。
</td></tr>


<tr>
<td rowspan=2>9</td>
<td>lddbl</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{DOUBLE}</td>
<td>17</td>
</tr><tr><td colspan=4>
载入一个 double 小数，并压入栈顶。<br>
{DOUBLE}：8位长整形字节组。
</td></tr>

<tr>
<td rowspan=2>10</td>
<td>ldint</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{LONG}</td>
<td>17</td>
</tr><tr><td colspan=4>
载入一个 long 整数，并压入栈顶。<br>
{LONG}：8位长整形字节组。
</td></tr>

<tr>
<td rowspan=2>11</td>
<td>ldstr</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{STR_LEN}{STR_BYTES}</td>
<td>13+N</td>
</tr><tr><td colspan=4>
载入一个字符串，并压入栈顶。<br>
{STR_LEN}: 字符串的字节长度。<br>
{STR_BYTES}:字符串的字节组。
</td></tr>



<tr><td colspan=5>运算符</td></tr>

<tr>
<td rowspan=2>12</td>
<td>add</td>
<td>+</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行相加，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>13</td>
<td>sub</td>
<td>-</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行相减，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>14</td>
<td>mul</td>
<td>*</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行相乘，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>15</td>
<td>div</td>
<td>/</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行相除，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>16</td>
<td>mod</td>
<td>%</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行模运算，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>17</td>
<td>eq</td>
<td>=</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行等于比较，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>18</td>
<td>neq</td>
<td>!=</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行不等于比较，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>19</td>
<td>gt</td>
<td>&gt;</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行大于比较，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>20</td>
<td>gte</td>
<td>&gt;=</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行大于等于比较，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>21</td>
<td>lt</td>
<td>&lt;</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行小于比较，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>22</td>
<td>lte</td>
<td>&lt;=</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行小于比较，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>23</td>
<td>not</td>
<td>!</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出一个对象进行非运算，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>24</td>
<td>and</td>
<td>&amp;&amp;</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行逻辑与运算，并将结果压入栈顶。
</td></tr>

<tr>
<td rowspan=2>25</td>
<td>or</td>
<td>||</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
从栈顶弹出两个对象进行逻辑非运算，并将结果压入栈顶。
</td></tr>

<tr><td colspan=5>系统</td></tr>

<tr>
<td rowspan=2>26</td>
<td>abort</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
终止当前文档的执行。
</td></tr>

<tr>
<td rowspan=2>27</td>
<td>exit</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}</td>
<td>9</td>
</tr><tr><td colspan=4>
结束整个当前事务的执行。
</td></tr>

</table>
