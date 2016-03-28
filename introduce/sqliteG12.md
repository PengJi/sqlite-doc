# Sqlite源代码介绍
<font face="微软雅黑" size="3px">

sqlite-src-3071401，版本为3.7.14.1，代码有四种模式，分别在不同状态下使用  
SQLITE_MUTEX_OMIT 不适用互斥体的代码，初始化时，静态互斥体结构体不被覆盖。  
SQLITE_MUTEX_NOOP 单线程应用时代码，没有提供互斥排它锁，初始化时，静态互斥体结构体被覆盖。  
SQLITE_MUTEX_PTHREADS UNIX 多线程调用的代码  
SQLITE_MUTEX_W32 WIN32下多线程调用的代码  
