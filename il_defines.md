#IL Defines

<table style="font-size:12px">
<tr>
<th>操作码</th>
<th>名称</th>
<th>符号</th>
<th>原形</th>
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
<td>dom</td>
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
从栈顶弹出一个对象并将该对象设置到变量组中。
{INDEX_STR_LEN}: 索引名称的字符串的字节长度。<br>
{STR_BYTES}:索引的字节组。
</td></tr>

<tr>
<td rowspan=2>8</td>
<td>call</td>
<td>N/A</td>
<td>{LINE}{SLINE}{OPCODE}{ARGS_LEN}{METHOD_STR_LEN}{STR_BYTES}</td>
<td>17</td>
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
<td rowspan=2>1</td>
<td>ldu_db</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>ldu_l</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>ldstr</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>ldm_i</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>call</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr><td colspan=5>运算符</td></tr>

<tr>
<td rowspan=2>1</td>
<td>add</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>sub</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>mul</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>div</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>mod</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>eq</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>neq</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>gte</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>lte</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>gt</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>lt</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>not</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>and</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>or</td>
<td>||</td>
<td>{LINE}{CODE}</td>
<td>5</td>
</tr><tr><td colspan=4>
将栈顶部的两个对象(尝试转换为bool类型)进行或操作并将结果推送到堆栈。
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>nil_c</td>
<td>??</td>
<td>{LINE}{CODE}</td>
<td>5</td>
</tr><tr><td colspan=4>
null 合并运算符。如果此运算符的左操作数不为 null，则此运算符将返回左操作数；否则返回右操作数。
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>exit</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>stloc</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>opp</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>ldcur</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>pop</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>inc</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>

<tr>
<td rowspan=2>1</td>
<td>line</td>
<td>N/A</td>
<td>{LINE}...</td>
<td>0</td>
</tr><tr><td colspan=4>
summary
</td></tr>


</table>
