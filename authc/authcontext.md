# 利用栈存储解析树的授权内容
<font face="微软雅黑" size="3px">

sqlite3AuthContextPush()和sqlite3AuthContextPop（）函数

利用AuthContext 结构体体申明栈信息，并利用栈存储解析树的授权内容(Parse.zAuthContext)，

结构体AuthContext 是一个在栈中申明并用来存储Parse.zAuthContext信息的结构体
<pre>
struct AuthContext {
  const char *zAuthContext;   /* 放置保存Parse.zAuthContext 在这里*/
  Parse *pParse;   /* 解析结构*/
};</pre>

sqlite3AuthContextPush()中栈PUSH(入栈)语句
<pre>pContext->zAuthContext = pParse->zAuthContext;
</pre>
sqlite3AuthContextPop()中栈pop（出栈）语句
<pre>pContext->pParse->zAuthContext = pContext->zAuthContext;</pre>
