# 删除vdbe结构体
<font face="微软雅黑" size="3px">

该功能由函数`void sqlite3VdbeFrameDelete(VdbeFrame *p){ }`实现。  
当程序运行完毕后，需要销毁VDBE。该函数嵌套调用了函数`qlite3VdbeFreeCursor(p->v， apCsr[i])`和函数`qlite3VdbeFreeCursor(p->v， apCsr[i])`。由函数的定义可以看出，在删除vdbe结构体时并不是将其真正的删除，而是先使用`qlite3VdbeFreeCursor(p->v， apCsr[i])`释放游标，接着调用`releaseMemArray(aMem， p->nChildMem)`释放Mem结构体数组，最终使用`sqlite3DbFree(p->v->db`， p)释放内存数组。
