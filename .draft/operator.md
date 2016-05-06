#运算符及优先级


<table>

<tr>
<td>级别</td>
<td>符号</td>
<td>说明</td>
<td>备注</td>
</tr>

<tr>
<td rowspan=2>0</td>
<td>&apos;</td>
<td>单引号。表示一个字符串。如：s=&apos;hello &quot;string&quot;&apos; </td>
<td>\&apos;表示单引号字符(转义)。</td>
</tr>
<tr>
<td>&quot;</td>
<td>双引号。表示一个字符串。如：s=&quot;hello &apos;string&apos;&quot; </td>
<td>\&quot;表示双引号字符(转义)。</td>
</tr>


<tr>
<td rowspan=3>1</td>
<td>()</td>
<td>小括号。(表达式)或function(参数)。</td>
<td></td>
</tr>
<tr>
<td>[]</td>
<td>中括号。array[下标]或indexer[参数]。</td>
<td></td>
</tr>
<tr>
<td>.</td>
<td>点。对象成员访问。</td>
<td></td>
</tr>

<tr>
<td rowspan=2>2</td>
<td>-</td>
<td>负号运算符。-表达式。</td>
<td></td>
</tr>
<tr>
<td>!</td>
<td>逻辑非运算符。!表达式。</td>
<td></td>
</tr>

<tr>
<td rowspan=3>3</td>
<td>*</td>
<td>乘。表达式 * 表达式。</td>
<td></td>
</tr>
<tr>
<td>/</td>
<td>除。表达式 / 表达式。</td>
<td></td>
</tr>
<tr>
<td>%</td>
<td>余数（取模）。表达式 % 表达式。</td>
<td></td>
</tr>

<tr>
<td rowspan=2>4</td>
<td>+</td>
<td>加。表达式 + 表达式。</td>
<td></td>
</tr>
<tr>
<td>-</td>
<td>减。表达式 - 表达式。</td>
<td></td>
</tr>


<tr>
<td rowspan=4>5</td>
<td>&gt;</td>
<td>大于。表达式 &gt; 表达式。</td>
<td></td>
</tr>
<tr>
<td>&gt;=</td>
<td>大于等于。表达式 &gt;= 表达式。</td>
<td></td>
</tr>
<tr>
<td>&lt;</td>
<td>小于。表达式 &le; 表达式。</td>
<td></td>
</tr>
<tr>
<td>&lt;=</td>
<td>小于等于。表达式 &le;= 表达式。</td>
<td></td>
</tr>

<tr>
<td rowspan=2>6</td>
<td>==</td>
<td>等于。表达式 == 表达式。</td>
<td></td>
</tr>
<tr>
<td>!=</td>
<td>不等于。表达式 != 表达式。</td>
<td></td>
</tr>

<tr>
<td rowspan=2>7</td>
<td>||</td>
<td>逻辑或。表达式 || 表达式。</td>
<td></td>
</tr>
<tr>
<td>&amp;&amp;</td>
<td>逻辑与。表达式 &amp;&amp; 表达式。</td>
<td></td>
</tr>

<tr>
<td rowspan=2>8</td>
<td>??</td>
<td>空运算符。表达式1 ?? 表达式2。</td>
<td></td>
</tr>
<tr>
<td>?:</td>
<td>条件运算符。条件 ? 表达式1 : 表达式2。</td>
<td></td>
</tr>

<tr>
<td>9</td>
<td>=</td>
<td>赋值运算符。变量 = 表达式。</td>
<td></td>
</tr>
<tr>

<tr>
<td>10</td>
<td>,</td>
<td>逗号运算符。表达式 , 表达式 , …。</td>
<td></td>
</tr>
<tr>

<tr>
<td>11</td>
<td>|</td>
<td>格式运算符。值 | name = 表达式 , …。</td>
<td>该表达式只能在输出标签中，如：{now | datetime='y-M-D'}</td>
</tr>
<tr>

</table>





