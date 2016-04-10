# SQLite不同模式的锁与实现
<font face="微软雅黑" size="3px">

文件中用于并发控制的文件加锁的方法有如下几种，支持基于数据库所在的文件系统自动选择适当的加锁风格。  
——POSIX locking (the default)，  
——No locking，  
——Dot-file locking，  
——flock() locking，  
——AFP locking (OSX only)，  
——Named POSIX semaphores (VXWorks only)，  
——proxy locking. (OSX only)
