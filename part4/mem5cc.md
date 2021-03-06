# mem5.c调用的C接口
<font face="微软雅黑" size="3px">

`sqlite3_config（int,...）`，此接口被用于改变SQLITE的全局变量，以便于当应用程序有特定需求时调整SQLITE。默认情况下不使用。括号中第一个参数是类型为整型的配置选项，确定 SQLite 要配置哪些属性，省略号处是后续参数，取决于第一个参数中的配置选项。  
当SQLite使用SQLITE_ENABLE_MEMSYS5选项编译时，memsys5就被包含在其中，一般情况下memsys5被禁用。若要启用零内存分配器，应调用SQLite接口`sqlite3_config(SQLITE_CONFIG_HEAP, pBuf, szBuf, mnReq)`，其中SQLITE_CONFIG_HEAP指定了一个静态内存缓冲区，pBuf指向一个大的连续的内存块，SQLite使用它满足所有的内存分配需要。  
pBuf也可以指向一个静态数组或一段从其他应用程序特定机制获取的内存。szBuf为pBuf内存的字节数。mnReq为一次分配的最小字节数。任何对sqlite3_malloc(N)的调用，当N小于mnReq时会向上舍入到mnReq。nmReq必须是2的幂。mnReq参数在Robson证明中对于减小n值和最小内存需求是至关重要的。  
memsys5分配器被设计用于嵌入式系统中，szBuf通常在几百KB到几十MB之间，取决于系统需要和内存预算。memsys5使用的算法可以概括为“2的幂，首次命中”。所有内存分配请求的大小都舍入到2的幂，分配时使用pBuf中第一个足够大的空闲内存块。

