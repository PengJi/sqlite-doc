# 快速使用SQLite
<font face="微软雅黑">

这里简要介绍了SQLite的使用方法.  
1. 建立一个新的数据库<br>
在shell或者DOS命令行下输入:"sqlite3 test.db". 这将建立一个新的名为"test.db"的数据库文件.(可以使用不同的数据库名)
在命令行提示符中输入SQL命令创建并分配数据库空间.
更多相关内容请参考第X章.  
2. 编写一个使用SQLite的示例程序
以下是一个演示如何使用SQLite的TCL接口的TCL程序.该程序通过执行SQL语句建立一个由两个参数定义的数据库.首先程序定位并执行第7行sqlite3命令打开并创建一个db对象。通过eval方法将SQL语句绑定到db对象并执行.最后关闭数据库连接.
```c
  #!/usr/bin/tclsh
  if {$argc!=2} {
  puts stderr "Usage: %s DATABASE SQL-STATEMENT"
    exit 1
  }
  package require sqlite3
  sqlite3 db [lindex $argv 0]
  db eval [lindex $argv 1] x {
    foreach v $x(*) {
      puts "$v = $x($v)"
    }
    puts ""
  }
  db close
```
下面是一个演示如何使用SQLite C/C++接口的C程序.<br>第一个参数表示数据库的名称,第二个参数表示需要执行的SQL语句.
```c
  #include <stdio.h>
  #include <sqlite3.h>

  static int callback(void *NotUsed, int argc, char **argv, char **azColName){
    int i;
    for(i=0; i&lt;argc; i++){
      printf("%s = %s\n", azColName[i], argv[i] ? argv[i] : "NULL");
    }
    printf("\n");
    return 0;
  }

  int main(int argc, char **argv){
    sqlite3 *db;
    char *zErrMsg = 0;
    int rc;

    if( argc!=3 ){
      fprintf(stderr, "Usage: %s DATABASE SQL-STATEMENT\n", argv[0]);
      return(1);
    }
    rc = sqlite3_open(argv[1], &db);
    if( rc ){
      fprintf(stderr, "Can't open database: %s\n", sqlite3_errmsg(db));
      sqlite3_close(db);
      return(1);
    }
    rc = sqlite3_exec(db, argv[2], callback, 0, &zErrMsg);
    if( rc!=SQLITE_OK ){
      fprintf(stderr, "SQL error: %s\n", zErrMsg);
      sqlite3_free(zErrMsg);
    }
    sqlite3_close(db);
    return 0;
  }
```
