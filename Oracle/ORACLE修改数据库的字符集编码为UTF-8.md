# ORACLE 修改数据库的字符集编码为UTF-8

## 参考引用

* [ORACLE 修改数据库的字符集编码为UTF-8](https://blog.csdn.net/shiyu1157758655/article/details/78748283)

## 运行环境

* 系统：Centos7
* 数据库：Oracle 11gR2

## 指令操作顺序

**修改指令操作**

```sql
SQL> shutdown immediate
数据库已经关闭。
已经卸载数据库。
ORACLE 例程已经关闭。
SQL> startup mount
ORACLE 例程已经启动。
Total System Global Area 3373858816 bytes
Fixed Size                  2180424 bytes
Variable Size            1946159800 bytes
Database Buffers         1409286144 bytes
Redo Buffers               16232448 bytes
数据库装载完毕。
SQL> alter system enable restricted session;
系统已更改。
SQL> alter system set job_queue_processes=0;
系统已更改。
SQL> alter system set aq_tm_processes=0;
系统已更改。
SQL> alter database open;
数据库已更改。
SQL> alter database character set internal_convert utf8;
```

**修改完成后操作**

```sql
SQL> shutdown immediate
数据库已经关闭。
已经卸载数据库。
ORACLE 例程已经关闭。
SQL> startup
ORACLE 例程已经启动。

Total System Global Area 3373858816 bytes
Fixed Size                  2180424 bytes
Variable Size            1946159800 bytes
Database Buffers         1409286144 bytes
Redo Buffers               16232448 bytes
数据库装载完毕。
数据库已经打开。
SQL> select userenv('language') from dual;

USERENV('LANGUAGE')

```
