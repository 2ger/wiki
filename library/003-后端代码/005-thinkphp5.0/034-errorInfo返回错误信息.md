# errorInfo() 返回错误信息
```
array PDOStatement::errorInfo  ( void )

```
PDOStatement::errorInfo() 返回一个关于上一次语句句柄执行操作的错误信息的数组 。该数组包含下列字段：

0 SQLSTATE 错误码
1 具体驱动错误码。
2 具体驱动错误信息。
```
/* 激发一个错误 --  BONES 数据表不存在 */
 $sth  =  $dbh -> prepare ( 'SELECT skull FROM bones' );
 $sth -> execute ();

echo  "\nPDOStatement::errorInfo():\n" ;
 $arr  =  $sth -> errorInfo ();
 print_r ( $arr );

```
输出
```
PDOStatement::errorInfo():
Array
(
    [0] => 42S02
    [1] => -204
    [2] => [IBM][CLI Driver][DB2/LINUX] SQL0204N  "DANIELS.BONES" is an undefined name.  SQLSTATE=42704
)

```
