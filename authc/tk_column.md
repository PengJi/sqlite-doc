# 验证解析树中TK_COLUMN表达式是否可访问
<font face="微软雅黑" size="3px">

函数说明
<pre>
void sqlite3AuthRead(
  Parse *pParse,        /* 解析上下文*/
  Expr *pExpr,          /*检查授权表达式*/
  Schema *pSchema,      /*表达式的模式 */
  SrcList *pTabList     /*可能引用的所有表*/
)</pre>

pExpr是一个检查TK_COLUMN表达式。

这个表所指的是pTabList否则它是在新或旧的触发器的表

工作流程

如果授权函数返回SQLITE_IGNORE,将TK_COLUMN指令改变成TK_NULL。

如果授权函数返回SQLITE_DENY,然后生成一个错误
