# 查询解析与授权
<font face="微软雅黑" size="3px">

给定一个SQL语句,SQL解析器主要任务是:  
(1)检查这个查询是否被正确地定义;  
(2)解决名字和引用;  
(3)将这个查询转化为优化器使用的内部形式;  
(4)核实这个用户是否被授权执行这个查询.



