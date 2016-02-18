# SQLite中B-tree的实现
<font face="微软雅黑" size="3px">

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;B-tree在SQLite中占有举足轻重的地位。SQLite的结构图如图1所示。B-Tree位于虚拟机和页缓存之间。虚拟机负责执行程序，负责操纵数据库文件。数据库的存储用B树实现。B树向磁盘请求信息，以固定大小的块。系统默认的块的大小是1024字节，块大小应在512字节到65536字节之间。B树从页缓存中请求页，当修改页或者提交，或者回滚操作时，通知页缓存。修改页时，如果使用传统的回滚日志，pager首先将原始页复制到日志文件。同样，page在B-tree完成写操作时收到通知，并基于所处的事务状态决定如何处理。
<img src="SQLiteBlockGraph.jpg">
