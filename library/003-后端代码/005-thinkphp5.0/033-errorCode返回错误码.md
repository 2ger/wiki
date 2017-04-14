# errorCode() 返回错误码
```
string PDOStatement::errorCode  ( void )

```
与 PDO::errorCode() 相同，只是 PDOStatement::errorCode() 只取回 PDOStatement 对象执行操作中的错误码。
;获取SQLSTATE错误码

/* 引发一个错误 --  BONES 数据表不存在 */
 $err  =  $dbh -> prepare ( 'SELECT skull FROM bones' );
 $err -> execute ();

echo  "\nPDOStatement::errorCode(): " ;
print  $err -> errorCode ();
输出
```
PDOStatement::errorCode(): 42S02

```
