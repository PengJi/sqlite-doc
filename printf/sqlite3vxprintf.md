# sqlite3VXPrintf()函数
 <pre>
 void sqlite3VXPrintf(
  StrAccum *pAccum,                  在这里积累的结果
  int useExtended,                   允许扩展转换为%
  const char *fmt,                   格式字符串
  va_list ap                         参数
)
</pre>
功能：将fmt给的一个字符串传进StrAccum对象中。<br>
实现方法：格式字符串的for循环。作用分别如下：
<br>1）找出出现的标识
<br>2）得到区域宽度
<br>3）得到区域精度
<br>4）得到转换类型修饰符
<br>5）得到区域信息入口
<br>6）终端切换格式类型（switch语句）
<br>7）转换的文本指向“bufpt”且有length这么长。
<br>8）区域宽度是"width"然后输出
<br>函数引用：<img src="p4.png">

