#columnCount() 返回结果集的列数
int PDOStatement::columnCount  ( void )
使用 PDOStatement::columnCount() 返回由 PDOStatement 对象代表的结果集中的列数。

如果是由 PDO::query() 返回的 PDOStatement 对象，则列数计算立即可用。

如果是由 PDO::prepare() 返回的 PDOStatement 对象，则在调用 PDOStatement::execute() 之前都不能准确地计算出列数。
```
;计算列数

$dbh  = new  PDO ( 'odbc:sample' ,  'db2inst1' ,  'ibmdb2' );

 $sth  =  $dbh -> prepare ( "SELECT name, colour FROM fruit" );

 /*  计算一个（不存在）的结果集中的列数 */
 $colcount  =  $sth -> columnCount ();
print( "Before execute(), result set has  $colcount  columns (should be 0)\n" );

 $sth -> execute ();

 /* 计算结果集中的列数 */
 $colcount  =  $sth -> columnCount ();
print( "After execute(), result set has  $colcount  columns (should be 2)\n" );

```
