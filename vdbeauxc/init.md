# 初始化vdbe
<font face="微软雅黑" size="3px">

该功能由函数`void sqlite3VdbeRewind(Vdbe *p) {}`实现。   程序在处理SQL之前，需要先对vdbe进行初始化。  
当vdbe被运行之后，使用该函数将虚拟机恢复到初始状态。Rewind函数主要执行了以下9个操作来将vdbe的各项参数初始化：
```c
 <br> p->pc = -1;
  p->rc = SQLITE_OK;
  p->errorAction = OE_Abort;
  p->magic = VDBE_MAGIC_RUN;
  p->nChange = 0;
  p->cacheCtr = 1;
  p->minWriteFileFormat = 255;
  p->iStatement = 0;
  p->nFkConstraint = 0;
```
从上面的参数可以看出，vdbe的初始化主要就是对内部的各种参数赋初值，从而使之回到初始状态。需要注意的是程序中至少要有一个操作码，即 assert( p->nOp>0 )。此外，还应尽早设置p->magic的值。
