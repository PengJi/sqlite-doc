# Wal的优缺点
<font face="微软雅黑" size="3px">

Wal的优点有：
* 读操作不会阻塞写操作，同时写操作也不会阻塞读操作。这事并发管理的“黄金准则”;<br>
* 在大多数操作场景中，与回滚日志相比，Wal相当快。<br>
* 磁盘I/O变的更可预见，并且引起更少的fsync()系统调用。因为所有的Wal写操作是线性写入日志文件，很多I/O变的连续并能够按计划执行。<br>

Wal存在的缺点：<br>

* 所有的处理被绑定到单个主机上。也就是说，不能再如NFS这样的网络文件系统上使用Wal。<br>
* 为满足Wal和相关共享内存的需要，使用WAL引入了两个额外的半持久性文件<yourdb>-wal和<yourdb>-shm.这对于那些使用SQLite数据库作为应用程序文件格式是不具有吸引力的。这也影响了只读环境，因为-shm文件必须是可写的，并且/或数据库所在目录也必须是可写的。
<br>
* 对于非常大的事务，WAL的性能将会降低。虽然WAL是一个高性能选项，但是非常大或运行时间非常长的事务会引入额外的开销<br>
