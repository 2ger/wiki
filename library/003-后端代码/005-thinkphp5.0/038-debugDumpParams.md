#  debugDumpParams() 打印SQL预处理命令
bool PDOStatement::debugDumpParams  ( void )
直接打印出一条预处理语句包含的信息。提供正在使用的 SQL 查询、所用参数（Params）的数目、参数的清单、参数名、用一个整数表示的参数类型（paramtype）、键名或位置、值、以及在查询中的位置（如果当前 POD 驱动不支持，则为-1）。

此为一个用于调试的功能，在正常输出的情况下直接输出数据。

和直接将结果输出到浏览器一样，可使用输出控制函数来捕获当前函数的输出，然后(例如)保存到一个 string 中。只打印此时此刻语句中的参数。额外的参数不存储在语句中，也就不会被输出。
```
/* 通过绑定 PHP 变量执行一条预处理语句 */
 $calories  =  150 ;
 $colour  =  'red' ;
 $sth  =  $dbh -> prepare ( 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < :calories AND colour = :colour' );
 $sth -> bindParam ( ':calories' ,  $calories ,  PDO :: PARAM_INT );
 $sth -> bindValue ( ':colour' ,  $colour ,  PDO :: PARAM_STR ,  12 );
 $sth -> execute ();

 $sth -> debugDumpParams ();

```
输出
```
SQL: [96] SELECT name, colour, calories
    FROM fruit
    WHERE calories < :calories AND colour = :colour
Params:  2
Key: Name: [9] :calories
paramno=-1
name=[9] ":calories"
is_param=1
param_type=1
Key: Name: [7] :colour
paramno=-1
name=[7] ":colour"
is_param=1
param_type=2

```
```
;使用未命名参数的例子

/* 通过绑定 PHP 变量执行一条预处理语句 */
 $calories  =  150 ;
 $colour  =  'red' ;
 $name  =  'apple' ;

 $sth  =  $dbh -> prepare ( 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < ? AND colour = ?' );
 $sth -> bindParam ( 1 ,  $calories ,  PDO :: PARAM_INT );
 $sth -> bindValue ( 2 ,  $colour ,  PDO :: PARAM_STR );
 $sth -> execute ();

 $sth -> debugDumpParams ();

```
输出
```
SQL: [82] SELECT name, colour, calories
    FROM fruit
    WHERE calories < ? AND colour = ?
Params:  2
Key: Position #0:
paramno=0
name=[0] ""
is_param=1
param_type=1
Key: Position #1:
paramno=1
name=[0] ""
is_param=1
param_type=2

```
