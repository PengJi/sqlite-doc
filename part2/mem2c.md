# 调试内存分配器（mem2.c）
<font face="微软雅黑" size="3px">

　　如果SQLite使用SQLITE_MEMDEBUG编译时选项来编译，则使用一个不同的、对系统malloc(), realloc()和free()进行重型包装的内存分配器。重型包装器对每个分配请求多分配100字节的额外空间，用来在分配的末尾放置哨兵值。当一个分配被释放时，检查这些哨兵值以确保SQLite内核没有超出缓冲区的两端。当系统库来自GLIBC时，重型包装器也会使用GNU backtrace()函数来检查栈，并记录malloc()调用的祖先函数。当运行测试套件时，重型包装器还会记录当前测试用例的名称。  
　　重型包装器只用于SQLite的测试、分析和调试。它有显著的性能和内存开销，一般不用在最终产品中。  
　　mem2.c中主要用于调试，增加了用于调试的附属结构。使用SQLITE_MEMDEBUG启用。测试基础设施通过使用一个特殊的检测内存分配器来验证SQLite没有错误地使用动态分配的内存。检测内存分配器通过编译时使用SQLITE_MEMDEBUG选项来激活，它比缺省的内存分配器更慢，因此不建议在产品中使用它。  
但是在测试时激活它，可以做以下检查：
1. 边界检查。检测内存分配器在每个内存分配的末尾放置哨兵值，以验证SQLite没有任何例程写出了分配的边界。
2. 释放后的内存使用。当每块内存被释放时，每个字节会填充一些无用的位模式。这可以确保内存在释放后绝不会留下曾经使用过的痕迹。
3. 从非malloc获取的内存的释放。每个来自于检测内存分配器的内存分配都含有一个哨兵值，以验证每个分配的释放来自于先前的malloc。
4. 未初始化的内存。检测内存分配器用一些无用的位模式初始化每块内存的分配，以确保用户不能对所分配内存的内容做任何假设。

　　无论是否使用检测内存分配器，SQLite都会跟踪当前已取出多少内存。有数百个测试脚本用于测试SQLite。在每个脚本的末尾，所有的对象被销毁，并有一段测试保证所有内存已释放。这就是检测内存泄漏的方法。注意内存泄漏的检测在任何时候都是大批量的进行，包括测试构建和产品构建过程中。每当一个开发者运行任意单个测试脚本，内存泄漏检测就会被激活。因此开发过程中引入的内存泄漏能够迅速地被检测到并修复。
内存分配器的结构如下：
	**  ------------------------------------------------------------------------
	**  | Title |  backtrace pointers |  MemBlockHdr |  allocation |  EndGuard |
	**  ------------------------------------------------------------------------
`Title`:用于描述这段内存，在出错时可以打印出来。  
`backtrace pointer`:用于保留调用堆栈。  
`MemBlockHdr`:负责这片内存的管理，以及串联unfree的MemBlock。  
`allocation`:分配给上层的空间。  
`EndGuard`:尾部的哨兵，用于检查内存被踩。  
还有个“HeadGaurd ”在MemBlockHdr中。  


