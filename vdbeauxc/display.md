# 显示部分
<font face="微软雅黑" size="3px">

该部分函数用来打印出程序运行过程中与SQL相关的语义及操作。  
（1）打印SQL语句  
该功能由函数`void sqlite3VdbePrintSql(Vdbe *p){}`来实现。  
（2）打印SQL中的IO跟踪消息  
该功能由函数`void sqlite3VdbeIOTraceSql(Vdbe *p){}`实现。  
