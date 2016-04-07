# 空操作内存分配器（mem0.c）
<font face="微软雅黑" size="3px">

该分配器通常是一个占位符，以便SQLite能链接一些不使用`malloc()`,`free()`或`realloc()`的自定义内存分配器。当需要调用一个分配器的时候，需要通过`sqlite3_config()`函数来配置。 特征：  
1. `SQLITE_ZERO_MALLOC`
利用该选项进行编译，缺省内存分配器就会失效。带`SQLITE_ZERO_MALLOC`选项编译的应用程序在使用SQLite之前，需要使用`sqlite3_config()`，结合`SQLITE_CONFIG_MALLOC`或`SQLITE_CONFIG_HEAP`来指定新的可选内存分配器。
2. 对函数的调用通常都会失败，并且返回0；

函数介绍：
```c
static void *sqlite3MemMalloc(int nByte){ return 0; }  
static void sqlite3MemFree(void *pPrior){ return; }
static void *sqlite3MemRealloc(void *pPrior,int nByte){return 0;}
static int sqlite3MemSize(void *pPrior){ return 0; }
static int sqlite3MemRoundup(int n){ return n; }
static int sqlite3MemInit(void *NotUsed){ return SQLITE_OK; }
static void sqlite3MemShutdown(void *NotUsed){ return; }
void sqlite3MemSetDefault(void) //这个文件中唯一与外部联系的例程

```

