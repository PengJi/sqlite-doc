#  缺省内存分配器（mem1.c）
<font face="微软雅黑">

这个文件包含了底层内存分配器，该分配器包含了标准的C函数库，比如`malloc/realloc/free`接口。当既没有定义`SQLITE_MEMDEBUG`，也没有定义`SQLITE_WIN32_MALLOC`时，`SQLITE_WIN32_MALLOC`被自动定义。
文件中包含的预处理宏：
`HAVE_MALLOC_USABLE_SIZE`
`SQLITE_WITHOUT_ZONEMALLOC`
`SQLITE_WITHOUT_MSIZE`
特征：
1. `SQLITE_SYSTEM_MALLOC`;
定义该分配器的宏。
2. 在每个`malloc()`分配的头部，多分配8byte保存分配的大小，以使用`memsize()`返回当前分配的大小；
3. `memsize()`还可跟踪未归还的内存字节数，它能确定当一个分配被释放时，能有多少内存从未归还的内存中移除；
4. 在大多数的应用程序中建议都使用这个缺省的内存分配器。

函数介绍
|编号|函数名|功能|
|--|--|--|
|1|static void *sqlite3MemMalloc(int nByte)|分配一块长度为nByte字节的连续区域|


