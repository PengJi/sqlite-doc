<font face="微软雅黑" size="3px">

具体定义如下：
1.  _SQLITEINT_H_  SQLite内部界面的定义；
2.	_LARGE_FILE 大文件
   _FILE_OFFSET_BITS 文件补偿位
   _LARGEFILE_SOURCE 宏_LARGEFILE_SOURCE必须在任一系统预处理命令#includes前出现。 因此，代码块必须在所有源文件中首先编码。
3.	引用标准库的头文件。
用 #include <config.h> 格式来引用标准库的头文件（编译器将从标准库目录开始搜索）。
用 #include “config.h” 格式来引用非标准库的头文件（编译器将从用户的工作目录开始搜索）。
4. 指令	#Pragma 是一种复杂的预处理指令，它的作用是设定编译器的状态或者  是指示编译器完成一些特定的动作。
其格式一般为: #pragma  para
其中para为参数
如：
  <br>#pragma message(“消息文本”)
 Message 参数能够在编译信息输出窗口中输出相应的信息。当编译器遇到这条 指令时就在编译输出窗口中将消息文本打印出来
    <br>#pragma warn -rch  不可达代码
   <br> #pragma warn -ccc  条件总是真或总是假
   <br> #pragma warn -aus  分配值从未用过
    <br>#pragma warn -csu  比较有符号和无符号
    <br>#pragma warn -spa  可疑的指针运算
禁止Borland编译器上的妨扰警告信号。
5.	_GNU_SOURCE
6. 如果定义了HAVE_STDINT_H，则要引用头文件stdint.h<br>
  如果定义了HAVE_INTTYPES_H，则要引用头文件inttypes.h
7.	这种情况，应该在GCC上运行
SQLITE_INT_TO_PTR(X)  整型到指针的转换
SQLITE_PTR_TO_INT(X)  指针到整型的转换
GCC：GNU编译器套件（GNU Compiler Collection）包括C、C++、Objective-C、Fortran、Java、Ada和Go语言的前端，也包括了这些语言的库（如libstdc++、libgcj等等）。
8.	SQLITE_THREADSAFE  宏SQLITE_THREADSAFE必须定义为'0','1'或者'2'
'0'表示互斥锁是永久无效的，并且库是没有安全威胁的。
'1'表示库是序列化的，线程安全的等级是最高级
'2'表示库可以多线程到多线程的使用，只要没有同时有2个线程使用相同的数据  库连接。
9.	SQLITE_POWERSAFE_OVERWRITE
10.	SQLITE_DEFAULT_MEMSTATUS
11.	为了指定哪一个内存子系统被使用，下面的其中一个宏被定义是正确的。
    SQLITE_SYSTEM_MALLOC 用标准系统的内存分配函数
SQLITE_WIN32_MALLOC 用win32自身的堆栈API
SQLITE_ZERO_MALLOC 用故障的根分配器
SQLITE_MEMDEBUG 系统调试版的内存分配函数
12.	SQLITE_MALLOC_SOFT_LIMIT  如果SQLITE_MALLOC_SOFT_LIMIT的值不是0，则保持可能的值下分配的内存大小。
13.	_XOPEN_SOURCE  为了启用在大多数UNIX操作系统上的递归互斥体， 我们需要将_XOPEN_SOURCE做定义
14.	引入头文件tcl.h    &nbsp;&nbsp;&nbsp;&nbsp;# include &lt;tcl.h&gt;
15.	NDEBUG   设置NDEBUG，通过禁止在代码中assert()语句的数目，让代码更小一些，运行速度更快一些。
    SQLITE_DEBUG   NDEBUG 和 SQLITE_DEBUG是相反的。
16.	testcase(X)  被用于帮助覆盖测试。
17.	TESTONLY(X)  宏TESTONLY被用来装入变量声明或其它小块的代码，这需要宏testcase() 和 assert()中参数的支撑。
18.	VVA_ONLY(X)  VVA_ONLY()中的代码将仅仅在验证过程期间运行。这些代码在assert()无效时/被禁止时被隐藏起来。
19.	ALWAYS(X)和NEVER(X)
宏ALWAYS 和 NEVER是为了保护代码而引入的。ALWAYS总是真的，NEVER总是假的。其目的是为了提高SQLite意外行为的恢复力。
20.	IS_BIG_INT(X)   这个宏用于testcase()宏变量内，来验证我们已经测试的SQLite是否支持大文件。
21.	likely(X)和unlikely(X)
宏likely()是一个暗示，即它所环绕的布尔表达式的值通常是真的。宏unlikely()是一个暗示，即它所环绕的布尔表达式的值通常是假的。
22.	OMIT_TEMPDB
如果SQLITE_OMIT_TEMPDB被定义了，OMIT_TEMPDB被设置为1，否则，设为0
23.	SQLITE_MAX_FILE_FORMAT 和SQLITE_DEFAULT_FILE_FORMAT定义了新数据库的缺省文件格式和库可以读的最大文件格式
24.	SQLITE_DEFAULT_RECURSIVE_TRIGGERS 决定触发器是否是默认递归。
25.	SQLITE_TEMP_STORE
26.	offsetof(STRUCTURE,FIELD)
27.	SQLITE_EBCDIC和SQLITE_ASCII
28.	typedef在计算机编程语言中用来为复杂的声明定义简单的别名，与宏定义有些差异。它本身是一种存储类的关键字，与auto、extern、mutable、static、register等关键字不能出现在同一个表达式中。如：
typedef　int　size;
此声明定义了一个int的同义字，名字为size
i64   8位有符号整型
u64   8位无符号整型
u32   4位无符号整型
u16   2位无符号整型
i16   2位有符号整型
u8    1位无符号整型
i8    1位有符号整型
29.	定义u64的最大值可以被存储在u32(4位无符号整型)中而且不丢失数据:
   <br>#define SQLITE_MAX_U32  ((((u64)1)<<32)-1)
30.	const常类型<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;常类型是指使用类型修饰符const说明的类型，常类型的变量或对象的值是不能被更新的。例如：const int Max=100; Max++会产生错误;
    extern可置于变量或者函数前，以表示变量或者函数的定义在别的文件中，提示编译器遇到此变量和函数时在其他模块中寻找其定义。

31.	SQLITE_BIGENDIAN<br>
SQLITE_LITTLEENDIAN<br>
SQLITE_UTF16NATIVE
32.	LARGEST_INT64   64位有符号整型可能的最大常量。
    SMALLEST_INT64   64位有符号整型可能的最小常量。
33.	ROUND8(x)
向上舍入一个数，使之接近8的倍数。这是用来强制8位对齐64位的体系结构。
34.	ROUNDDOWN8(x) 最接近8的倍数的四舍五入。
35.	EIGHT_BYTE_ALIGNMENT(X)  声明指针X是对齐到8字节边界的。这个宏只在assert()中用来验证代码是否得到了正确的对齐限制。
36.	定义一个结构的一般形式为：<br>
    struct结构名<br>
    {<br>
    //成员表列<br>
    };<br>
成员表由若干个成员组成， 每个成员都是该结构的一个组成部分。对每个
成员也必须作类型说明，其形式为：
    类型说明符 成员名;
    定义结构体BusyHandler
    用于存储繁忙的处理器回调给SQLite的一个处理。
37.	MASTER_NAME  主数据库表名
    TEMP_MASTER_NAME  临时数据库表名
38.	MASTER_ROOT  主数据库表的根页。
39.	SCHEMA_TABLE(x) 模式表表名。
40.	ArraySize(X) 可以返回数组中元素的个数。
41.	SQLITE_DYNAMIC
42.	SQLITE_WSD<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当SQLITE_OMIT_WSD被定义时，这就意味着目标平台不支持全局可写变量，例如全局变量和静态变量。 所有变量都必须是在堆栈上或从堆中动态分配的。当WSD不支持时，遍布在SQLite代码中的变量声明必须变成常数代替。宏SQLITE_WSD就是用来达到这个目的的。
43.	抑制编译器警告<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   UNUSED_PARAMETER(x)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UNUSED_PARAMETER2(x,y)<br>
44.	给结构体取别名<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  typedef struct AggInfo AggInfo;
45.	结构体Db<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   结构体Db的定义：系统所访问的每一个数据库文件都是此结构体的一个实例,通常在sqlite.aDb数组中会有两个这样的结构体，aDb[0]中存放的是主要的数据库文件，aDb[1]是用于保存临时表的数据库文件。
46.	Schema 结构体<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   结构体的一个实例存储的是数据库的模式。大多数的模式对象都与树相关，只有TEMP数据库模式例外，它不需要其他结构的支撑。在共享缓存模式下，一个单一的模式对象可以为指向同一个底层BtShared对象的多个B树所共享。当没有B树引用该模式对象的时候，该模式对象将被系统自动释放，但是TEMP模式对象需要利用sqlite3_close()函数来手动释放。线程必须拥有相应的B树互斥才可以访问模式的内容。
47.	Lookaside<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    Lookaside结构体拥有后备动态内存分配子系统的配置信息。 malloc全称是memory allocation,即动态内存分配，无法知道内存具体位置的时候，想要绑定真正的内存空间，就需要用到动态的分配内存。后备动态内存分配是利用一组固定大小的缓冲区，可以用来满足一个特定数据库连接对象的小的即时内存分配请求。后备动态内存缓冲区的使用使得SQLite的性能有显著的提高，避免SQL语句解析时的大量的动态内存分配或释放。在后备内存分配子系统中的每一个可用的内存分配空间都是存储在结构体类型LookasideSlot对象的链接列表中。即：<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;struct LookasideSlot {<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;LookasideSlot *pNext;  <br> /* pNext是一个LookasideSlot结构体类型的指针，指向的是空间缓冲区列表中的下一个可用缓冲区*/<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;};<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 注意，只允许对与特定的数据库连接相关联的对象进行后备动态内存分配。
    所以，模式信息不能存储在后备内存区里，因为在共享cache模块中模式信息是被多个数据库连接所共享的。因此，当解析模式信息时，Lookaside.bEnabled标志将会被清除，来保证后备内存分配不会被用来构建模式对象。
48.	Module结构体<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    每个SQLite的模块（虚拟表定义）由此的结构体的一个实例来定义，并存储在sqlite3.aModule哈希表中。其中的成员变量分别定义了回滚指针、传递给create_module()函数的名字、将pAux传递给create_module()函数以及模块析构函数。
49.	FuncDef结构体<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    每个SQL函数都是由以下结构体的一个实例来定义。指向以下结构的指针被存储在sqlite.aFunc哈希表中，当有多个函数重名的时候，哈希表指向的是这些结构体的一个链接列表。
50.	VTable结构体<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    为数据库模式中存在的每一个虚拟表创建一个该类型的对象，若数据库模式是共享的，那么使用这个共享模式的每一个数据库链接都会有一个这个结构体类型的实例，这是因为，每个数据库连接需要其自己的唯一sqlite3_vtab*手柄的实例来访问虚拟表的实现。sqlite3_vtab*手柄不能被数据库连接之间共享，即使当存储器内的数据库模式的其余部分是共享的，因为在内部初始化的时候，通过xConnect() 或 xCreate()将数据库链接句柄传递给其实现。这个数据库链接句柄或许将会被虚拟表的实现所用，用于访问在数据库中的实表，所以他们将会作为调用者事务处理的一部分，这些访问需要通过相同的数据库连接来实现，就像在虚拟表上执行SQL操作一样。在一个共享数据库模式中对应于单个表的所有VTable对象开始都被储存在由相应表对象的成员变量 Table.pVTable所指向的一个链接表中。当一个sqlite3_prepare()操作需要访问虚拟表，它会查找与数据库链接相对应的的VTable的列表，为在编译查询时使用正确的sqlite3_vtab*句柄做准备。当在内存中的表对象被删除（例如，当模式由于某种原因被重新加载），则虚函数表的对象不会被立刻删除，sqlite3_vtab*句柄也不会立即断开链接，相反，它们会从Table.pVTable列表移动到另一个由相应的sqlite3结构体的sqlite3.pDisconnect成员开头的链接列表中，它们然后会被sqlite3*执行的一条语句在下一次删除或者是断开链接，这样做是为了避免涉及多个sqlite3.mutex互斥死锁问题。
51.	Savepoint结构体<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   目前所有的保存点都存储在一个以sqlite3.pSavepoint开始的链接列表中,在列表中的第一个元素是最近打开的保存点,保存点通过VDBE OP_Savepoint指令被添加到该列表。
52.	struct Column结构体<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  一个SQL表的任何一个列信息都被保存在此结构体类型的一个实例中。
53.	FKey结构体<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   每一个外键约束都是此结构体的一个实例。外键与两个表关联， “从”表是创建外键并且包含REFERENCES子句的表。在“到”表是在references子句中命名的表。 如：

    CREATE TABLE ex1(<br>
    a    INTEGER   PRIMARY KEY,<br>
    b    INTEGER   CONSTRAINT  fk1  REFERENCES ex2(x)<br>
    );<br>
对于外键“fk1”，“ex1”是从表，“ex2”是到表。<br>
    每一个REFERENCES字句都会产生一个附属于从表的该结构体的一个实例，当从表被创建的时候到表是不需要存在的，不检查到表的存在性
54.	Index结构体<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   每个SQL索引由此结构体的一个实例表示在存储器中，表中的要被索引的列由这种结构的aiColumn[]表示，当Index.onError=OE_None,意味着不是一个唯一性索引，否则它就是一个唯一性索引。 Index.onError的值表明了当试图插入一个非唯一性元素的时候应该采取哪种冲突处理算法。其中的成员变量定义了索引的名字、被索引的SQL表、为每一列的近似值做字符串定义、用相同的表相关联的下一个索引、为索引名字进行排序的排序序列数组、通过该索引使用的表的列数、在数据库文件中包含该索引的根的页、aSample[] 中的元素数目、不在aSample数组中的键值的平均nEq值以及最左边键的值。
55.	IndexSample结构体<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   其中包含的成员变量定义了文本或者是二进制大对象的字节长度、键与该样本相同的行的Est. number、键少于该样本的行的Est. number以及少于该样本的不重复的键的Est. number。存储在sqlite_stat3表中的每个样本值均使用这种类型的结构表示在存储器中。
56.	AggInfo结构体<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 这种结构体的一个实例包含了需要为选择语句生成代码的信息，这个选择中包含聚合函数。
若Expr.op==TK_AGG_COLUMN或Expr.op==TK_AGG_FUNCTION，那么Expr.pAggInfo是指向该结构体的指针。 Expr.iColumn字段是AggInfo.aCol[]或者AggInfo.aFunc[]中需要为该结点生成代码的信息的索引AggInfo.pGroupBy以及AggInfo.aFunc.pExpr指向描述选择语句，并包含在原始选择结构中的字段。当AggInfo结构体被释放的时候，这些字段不需要被释放。
57.	<br>#if SQLITE_MAX_VARIABLE_NUMBER<=32767
<br>typedef i16 ynVar;
<br>#else
<br>typedef int ynVar;
<br>#endif
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;数据类型ynVar是16位或32位的有符号整数，通常是16位，但是如果SQLITE_MAX_VARIABLE_NUMBER大于32767，必须使用32位。16位是首选，因为在Expr对象中这种方式占用更少的内存，包含很多预处理语句的Expr对象是系统内存使用的大用户。没有应用程序需要10个或者20个以上的变量，但是有些极端用户需要超过32767个变量的预处理语句，并且在编译阶段它们的请求是可被允许的。
58.	<br>#define OE_None    0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;没有约束需要检查
<br>#define OE_Rollback 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;操作失败，事务回滚
<br>#define OE_Abort    2  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;撤销更改，但是不回滚事务
<br>#define OE_Fail     3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;停止操作，保持先前更改
<br>#define OE_Ignore   4	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;忽略错误，不做插入或者更新
<br>#define OE_Replace  5&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	删除存在的记录，然后执行插入或者更新操作
<br>#define OE_Restrict 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<br> OE_Abort针对IMMEDIAT型，OE_Rollback针对DEFERRED型
<br>#define OE_SetNull  7	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将外键的值置为空
<br>#define OE_SetDflt  8	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将外键设置为默认值
<br>#define OE_Cascade  9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	级联更改
<br>#define OE_Default  99&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	执行任何默认操作<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SQLite支持许多不同的方法来处理约束错误。回滚处理意味着违反约束导致在进程失败的操作和当前事务被回滚。ABORT操作是指正在处理中的操作失败，并且该操作之前的所有更改均回滚，但是事务不回滚。FAIL处理是指正在进行的操作停止，并返回错误代码，但由于同样的操作而造成的之前的更改都不会改变，没有发生回滚。IGNORE是指导致约束错误的特定行不被插入或更新。处理继续，并且不返回错误。REPLACE是指违背唯一性约束的在数据库中先前存在的行被删除，从而新的插入或者更新操作可以进行，操作继续，不报告错误。RESTRICT, SETNULL, 以及CASCADE操作是适用于外键，RESTRICT就像是ABORT对于IMMEDIATE外键，以及ROLLBACK对于DEFERRED键，SETNULL是指外键被置为空。级联意味着所涉及到的表行的删除或更新操同时影响到包含外键的行。
59.	Token结构体<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;来源于词法分析器的每个记号都是这个结构体的一个实例。记号也作为表达式的一部分使用。注意,若Token.z==0，那么Token.dyn和Token.n是未被定义的，并且很可能包含随机值。当 Token.z==0时，不要对Token.dyn和Token.n做任何假设。
60.	结构体Expr<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;表达式可为SQL函数，子选择，子查询等。在数据看架构时Expr对象会使用大量的内存空间，为了帮助减少内存分配需求，有时一个对象会被截断。为了减少存储器分配的数量，有时两个或更多的对象会被存储在一个内存单元。Expr.op是操作码。整数解析器表示在这里代码重用为操作码。例如，解析器定义整数代码TK_GE代表>=操作符。相同的整数代码被重用来表示在表达式树中大于或等于操作数。如果表达式是一个SQL文字(TK_INTEGER,TK_FLOAT,TK_BLOB或TK_STRING),那么Expr.token包含SQL文字的文本。如果表达式是一个变量(TK_VARIABLE)，那么，Expr.token包含了变量的名字。最后，如果该表达式是一个SQL函数(TK_FUNCTION)，那么Expr.token包含了函数的名称。Expr.pRight和Expr.pLeft是一个二元运算符左边和右边的子表达式。一个或者两个都可以为空。如果 表达式是一个SQL函数，Expr.x.pList是参数列表。如果表达式是一个子查询，Expr.iColumn记录包含子查询结果的整数寄存器号。如果子查询提供了一个恒定的结果，那么iTable为-1。如果子查询在语句处理过程中不同时间的结果不一样，那么iTable是计算子查询的子程序的地址。<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;其中flags位的各种标志的含义：<br>
EP_FromJoin	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;起源于连接的ON或USING语句
<br>EP_Agg&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;包含了一个或多个聚合函数
<br>EP_Resolved&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;标识已经被解析到列
<br>EP_Error&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;表达式包含一个或多个错误
<br>EP_Distinct 			&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  有DISTINCT关键字的聚合函数
<br>EP_VarSelect		 <br>pSelect&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;是  相关的，不是持续的
<br>EP_DblQuotedtoken.z&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;源自于"..."
<br>EP_InfixFunc &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;适合于中缀功能:LINKE,GLOB等
<br>EP_ExpCollate&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;排序序列明确规定
<br>EP_FixedDest 		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;结果需要保存在一个特定的寄存器
<br>EP_IntValue &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;包含在u.iValue的整数值
<br>EP_xIsSelect  		<br>x.pSelect&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;是有效的(否则x.pList是)
<br>EP_Hint &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;未使用
<br>EP_Reduced   		Expr结构体是唯一的EXPR_REDUCEDSIZE字节
<br>EP_TokenOnly 		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Expr结构体是唯一EXPR_TOKENONLYSIZE&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;字节
<br>EP_Static  			&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;保存在内存中没有用malloc()获得
61.	结构体ExprList<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;表达式列表，每个表达式可以有一个名称，表达式可以用于几个方面。比如在SELECT之后的“expr AS ID”列表中，或在UPDATE中的"ID=expr"列表。结构体中定义了列表中的表达式数目、与ExprList相关的VDBE游标、列表中的每个表达式、表达式的列表、与此表达式相关的符号、一个指示何时处理完毕的标志、对于ORDER BY，结果集中的列数。
62.	结构体ExprSpan<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;解析器用这种结构的一个实例来记录,表达式的解析树和表达式输入文本的跨度。<br>
struct ExprSpan {<br>
&nbsp;&nbsp;  Expr *pExpr;          	/*表达式解析树*/<br>
  &nbsp;&nbsp;&nbsp;const char *zStart;   		/*输入文本的第一个字符*/<br>
     &nbsp;&nbsp; const char *zEnd;     	/*输入文本的最后一个字符*/<br>
}；
63.	结构体IdList<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这种结构的一个实例可以容纳一个简单的标识符列表,如在下面这些语句中的"a,b,c"列表:<br>
INSERT INTO t(a,b,c) VALUES ...;<br>
CREATE INDEX idx ON t(a,b,c);<br>
CREATE TRIGGER trig BEFORE UPDATE ON t(a,b,c) ...<br>
表名在INSERT语句中IdList代表列名的列表时，IdList.a.idx被使用。如果"a"是表"t"的第k列，那么IdList.a[0].idx==k。<br>
struct IdList {<br>
 &nbsp;&nbsp; struct IdList_item {<br>
   &nbsp;&nbsp; char *zName;      	/*标识符的名称*/<br>
   &nbsp;&nbsp; int idx;<br>
  } *a;<br>
 &nbsp;&nbsp; int nId;         			/*列表中标识符的数目*/<br>
};

64.	结构体SrcList<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;描述了一个SELECT语句中的FORM子句，在FORM子句中的每个表或子查询是SrcList.a[].array的一个独立元素。在多个数据库的支持下，下面的结构也可以用来描述一个特定的表，如由一个INSERT,DELETE,UPDATE自己修改的表。在标准的SQL中，这样的表必须有一个简单的名字:ID。但是在SQLite中，表现在可以通过一个数据库名，一个点甚至表名来确认。jointype表明在列表中这个表和下个表的连接类型。解析器用这种方式构建列表，但是sqlite3SrcListShiftJoinType()以后改变jointypes使得每个jointype表示这个表和上个表之间的联系。在colUsed字段，如果表包含多于63列和64列或更高列被使用，高位(63位)被设置。<br>
SrcList.a.jointype字段的允许值及其表示的含义：<br>
JT_INNER&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;任何内部或交叉连接
<br>JT_CROSS&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;明确使用了CROSS关键字
<br>JT_NATURAL&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;真正的"自然"连接
<br>JT_LEFT	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;左外连接
<br>JT_RIGHT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;右外连接
<br>JT_OUTER&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;存在"OUTER"关键字
<br>JT_ERROR&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;未知或不支持的连接类型
65.	结构体WherePlan<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这个结构的对象是在不透明的where.c模块外的。它只包括这里所以编译器会知道它的大小，没有在此对象中的字段应在where.c模块外使用。在连接中，pIdx仅用于当wsFlag和WHERE_INDEXED是真，pTerm仅用于当wsFlags和WHERE_MULTI_OR是真，pVtabIdx仅用于当wsFlags和WHERE_VIRTUALTABLE是真，永远不会多于一个条件为真。
66.	结构体WhereLevel<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;对于  在WHERE子句中实现的每个嵌套循环中，Whereinfo结构包含一个单一实例的结构，这个结构对where.c模块是私有的，不应该访问或通过其他模块进行修改。pIdxInfo字段用于帮助挑选最好的虚拟表索引，pIdxInfo指针包含FORM子句第i个表重新排序前的索引信息。whereInfoFree()在where.c中时释放所有pIdxInfo指针。每个FORM子句元素都有一  个WhereLevel。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;适合sqlite3WhereBegin()的wctrlFlags参数和WhereInfo.wctrFlags成员的标志的含义：<br>
WHERE_ORDERBY_NORMAL&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;无操作
<br>WHERE_ORDERBY_MINORDER BY &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;		处理min()函数
<br>WHERE_ORDERBY_MAXORDER BY&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;		处理max()函数
<br>WHERE_ONEPASS_DESIRED				&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;想一次通过的UPDATE/DELETE
<br>WHERE_DUPLICATES_OK					&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;不止一次确认返回的行
<br>WHERE_OMIT_OPEN_CLOSE&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;				表指针已经打开
<br>WHERE_FORCE_TABLE					&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;不要仅使用索引搜索
WHERE_ONETABLE_ONLY				&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;仅对pTable的第一个表进行编码
<br>WHERE_AND_ONLY 						&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;不要对OR使用指数
67.	结构体WhereInfo<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这个结构体定义了Where语句的一些信息。Where子句处理程序有两个部分，第一部分处理Where循环的开始，第二部分处理Where循环的尾部。
68.	结构体NameContext<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NameContext定义了解决表和列名的上下文，上下文包含了表(pSrcList)的列表字段和命名表达式列表(pEList)，命名表达式列表有可能是空。pSrc对应于一个SELECT中的FROM子句，或者表正由INSERT,UPDATE,DELETE操作，pEList对应于SELECT的结果集，对其他声明来说是空。NameContexts可以嵌套，当解析名称时，在最里面的上下文将被第一搜索。如果没有找到匹配，下一个外部环境进行检查，如果仍然没有匹配，检查下一个上下文，这一过程继续直到找到一个匹配或者所有上下文都检查，当找到一个匹配，包含该匹配上下文的nRef成员增加。
69.	结构体Select<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;结构的实例包含需要生成的一个SELECT语句代码的所有信息。如果没有LIMIT子句，nLimit设置为-1.nOffset设置为0。如果有一个LIMIT子句，分析器设置nLimit为限制的值，nOffset为偏移值(如果没有偏移为0)。但后来，nLimit和nOffset成为在VDBE中记录限制和偏移计数器的内存位置。
Select.setFlags的允许值("SF"前缀代表"Select Flag"):<br>
<br>SF_Distinct	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;输出应该不同
<br>SF_Resolved	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;标识符已经解析
<br>SF_Aggregate				&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;包含聚合函数
<br>SF_UsesEphemeral			&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;使用OpenEphemeral操作码
<br>SF_Expanded 				<br>sqlite3SelectExpand()&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;调用这个函数
<br>SF_HasTypeInfoFORM		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;子查询有Table元数据
<br>SF_UseSorter			&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;排序使用分拣机
<br>SF_Values				&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;从VALUES子句合成
70.	结构体TriggerPrg<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;以下结构体的实例为每个触发器创建，当执行INSERT,UPDATE,DELETE是有可能触发触发器。所有这些对象存储在Parse.pTriggerPrg为首的链表，一旦语句编译完成就删除这些对象。
71.	结构体Parse<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SQL解析器上下文。这种结构的副本通过解析器和分解为所有解析器操作例程，以携带整个全局解析信息。结构分为两部分。当解析器和代码生成递归调用它们自身，该结构的第一部分是不变的，但是第二部分在每个递归开始和结束时被复位。nTableLock和TableLock变量仅当启用共享缓存特性(当sqlite3Ted()->useShareDate为真)时使用，它们用来存储一组表锁需要的被编译语句。
72.	结构体TriggerStep<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;TriggerStep结构的一个实例用于存储触发器程序一部分的单个SQL语句。TriggerStep结构的一个实例存储在一个通过引用与此相关的Trigger结构的实例的"step_list"成员的单链表(使用"pNext"成员连接) 。该链表的第一个元素是触发程序的第一步。"op"成员表示这是否是一个"DELETE", "INSERT", "UPDATE" 或"SELECT"	语句，其他成员的含义是由如下的“OP”的值确定：<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;op == TK_INSERT
orconf->存储ON CONFLICT算法<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pSelect->如果这是一个INSERT INTO ... SELECT...语句，那么这个存储的指针SELECT语句。否则NULL。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;target -> 标记持有插入表的引用名<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pExprList ->如果这是一个 INSERT INTO ... VALUES ... 语句，那么这个存储要插入的值。否则NULL<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pIdList   ->如果这是一个INSERT INTO ... (<column-names>) VALUES ... 语句，那么这个存储要被插入的列名<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;op == TK_DELETE
target->标记持有进行删除的表的引用名称<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pWhere->指定DELETE语句的WHERE子句<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;op == TK_UPDATE
target->标记持有更新行的表的引用名<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pWhere->指定UPDATE语句的WHERE子句<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pExprList -> 更新的列的列表和更新它们的表达式<br>
73.	结构体Sqlite3Config<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;包含SQLite数据库全局配置数据的结构，此结构还包含一些状态信息，比如启用内存状态、启用核心互斥状态、启用完整的互斥锁、默认的后备缓冲区大小、默认后备缓冲区计算器、堆存储空间、最小堆和最大堆的要求大小、暂用缓存的大小和数量、解析器堆栈的最大深度等。
74.	结构体 Walker<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  上下文指针通过步行树遍历。该结构体定义了回调函数表达式，分析器上下文，子查询数，命名上下文的结构体，最后从语法树遍历的结点和他们的回调函数返回代码。
75.	VDBE程序的由来<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;编译器的输入是一个单独的 SQL 命令，输出是最终经过优化的 VDBE 程序。这些工作在 3 个阶段上完成：分词器(Tokenizer)、分析器(Parser)和代码生成器(Code Generator)。
分词器(Tokenizer):
编译的第一步是对 SQL 命令分词。分词器将一个命令分解成一串单独的词
汇(token)。词可以是有特定含义的一个字符或一个字符序列。每个词都有其关联的词类(token class)，词类是一个数字标识，表明这个词是什么。例如左括号的词类是 TK_LP，保留字 SELECT 的词类是 TK_SELECT。所有词类在 parse.h中定义。总之，分词器按照 SQL 的词法定义把它切分为一个一个的词，并传递给分析器(Parser)进行语法分析(忽略空格)。
     分析器(Parser):
 SQLite 的语法分析器是用 Lemon 生成的(Lemon 是一个开源的 LALR(1)语法分析器的生成器，SQLite 在使用时进行了定制)。该分析器用 parse.c 内定义的语法规则将一串词组织成层次结构的分析树(parse tree)。
Parse是Lemon生成的分析器的核心例程。在分析器调用ParseAlloc后，分词器就可以将切分的词传递给Parse，进行语法分析。SQLite对应的函数如下：
     Void  sqlite3Parser( void *yyp,   int yymajor,  sqlite3ParserTOKENTYPE yyminor ，
 sqlite3ParserARG_PDECL)<br>
该函数由sqlite3RunParser调用：<br>
    int sqlite3RunParser(Parse *pParse, const char *zSql, char **pzErrMsg)<br>
　　sqlite3RunParser位于token.c文件中，它是进行SQL语  句分析的入口，它调用sqlite3GetToken对SQL语句zSql进行分词，然后调用sqlite3Parser进行语法分析。而sqlite3Parser在语法规则发生规约时调用相应的opcode生成子例程，生成opcode。
代码生成器(Code Generator)：
代码生成器是 SQLite 中最庞大、最复杂的部分。与其它模块不同，代码生成器没有定义明确的接口，但它与分析器关系紧密。代码生成器由多个源文件组成，这些源文件大多针对特定的 SQL 操作。例如，生成 SELECT 语句的代码在 select.c 中，其它的源文件包括 update.c、insert.c、delete.c 和 trigger.c 等等。代码生成器根据语法分析树生成 VDBE 程序。树的每一部分生成一个 VDBE指令序列来完成特定的任务。代码生成器不仅负责生成代码，也负责进行查询优化。优化是代码生成的一部分，主要的实现位于 where.c 中。生成的 WHERE 子句通常被其它模块共享，比如 select.c、update.c 和delete.c。这些模块调用 sqlite3WhereBegin()开始 WHERE 语句块的指令生成，然后将返回的代码加入到它们自己的 VDBE 代码中，最后调用 sqlite3WhereEnd()，生成结束 WHERE 子句代码的 VDBE 指令。
76.	lemon语法分析生成器<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Lemon是一个C或者C++语言的LALR(1)语法分析器生成器。它和“bison”与“yacc”的功能是一样的，但它不是“bison”或者“yacc”的简单复制。为了减少编写代码的错误，它使用了一种不同的语法。Lemon使用了一种更为高级的分析引擎，运行速度比“bison”与“yacc”要更快，并且该引擎是可重入的和线程安全的。更进一步的，Lemon实现了能够消除资源泄漏的特性，适合于长时间运行的程序例如GUI或者嵌入式控制器中。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Lemon是一个类似于YACC的LALR(1)语法分析器，相对于YACC，它具有如下优势：<br>
Lemon生成的解析器是可重入和线程安全的；<br>
Lemon引入了非终结符析构器的概念，使得写一个不会产生内存泄漏的解析器更容易。<br>
操作的原理：<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;lemon的主要目标是把一个特定语言的上下文无关文法（CFG）翻译成C语言实现的该语言的语法分析器。程序有两个输入：<br>（1）语法规范<br> （2）分析器模板文件。<br>程序员只需提供语法规范即可。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Lemon自带了一个语法分析器模板，这对大多数的应用足够了。如果需要的话，用户可以替换一个新的分析器模板文件。  根据命令行参数，Lemon会产生下面文件中的一个到三个：
<br>（1）分析器的C语言代码；<br>
（2）一个头文件，为每个终结符定义了一个整型ID；<br>
（3）描述产生的语法分析器的状态的信息文件。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;默认情况下，上面的三个文件都会产生。如果使用了“-m”选项，则不会产
生头文件；如果使用“-q”选项，信息文件则不会产生。语法规范文件是一个以
“.y”为后缀的文件。在文档的例子中，设定规范文件的名称是“gram.y”。典型的使用方式是：
   &gt;lemon gram.y<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;上面的命令会产生“gram.c”、“gram.h”、“gram.out”三个文件。第一个就是语法分析器，第二个就是为所有的终结符定义了数值的头文件，最后一个是分析器使用的状态自动机的说明。完整的源代码包含在两个文件中，lemon.c本身就是产生器本身。一个单独的文件lempar.c是lemon产生语法分析子程序需要的模板文件。也可获取lemon的有关文档。





