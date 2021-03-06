# mem5.c功能概述
<font face="微软雅黑" size="3px">

SQLite通过动态内存分配来获取各种对象（例如数据库连接和SQL预处理语句）所需内存、建立数据库文件的内存Cache、以及保存查询结果。  
SQLite内核和它的内存分配子系统提供了与其他数据库不同的特性，使得SQLite在更多领域得以应用，这些特性有：
1. 对内存分配失败的健壮处理；
2. 无内存泄漏；
3. 内存使用限制；
4. 零分配选项；
5. 应用程序提供内存分配器；
6. 对防止内存分配失败或堆内存出现碎片提供形式化的保证；
7. 内存使用统计；
8. 尽量少调用分配器；
9. 开放式存取。  

memsys5是不使用malloc()的可选内存分配器，被称为零内存分配器。零内存分配器在启动时给SQLite提供几大块内存缓冲区，SQLite将用这些缓冲区作为它所有内存分配的需要，不再调用系统的malloc()和free()。memsys5将所有内存分配请求的大小都向上舍入至2的幂，使用内存中第一个足够大的空闲内存块。整体使用buddy算法来合并相邻的空闲内存块，为避免内存碎片和内存崩溃提供数学保证。

