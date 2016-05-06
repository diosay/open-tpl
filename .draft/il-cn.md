### IL
产品名称 版本 编码 生成日期   头结束行号 原模板文件      结束符（二进制的空表示字符串结束）
OTPL-IL  02   0    2012320923 xxxx       ./views/ax.otpl 0
...HEAD
IL行号 原文件行号 IL类型 块结束行号 块标题 结束符
xxxx   xxxx       block  xxxx       'id'   0
...
xxxx xxxx nop // end block
xxxx xxxx nop // HEAD-END
xxxx xxxx LAYOUT xxxx './views/layout.otpl''
...
xxxx xxxx END


编码:枚举值{
	0 UTF-8   //默认
	1 UNCODE
	2 ...
}


IL格式
9字节 变长

Nop
Prt Print
Jmp Jump
Jmp_c Jump_c
bin binary