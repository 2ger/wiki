# fetchColumn() 返回结果集中的下一行单独的一列
string PDOStatement::fetchColumn  ([ int $column_number  = 0  ] )
$column_number 从行里取回的列的索引数字。）。如果没有提供值，则 PDOStatement::fetchColumn() 获取第一列
从结果集中的下一行返回单独的一列，如果没有了，则返回 FALSE 。
```
;返回下一行的第一列

$sth  =  $dbh -> prepare ( "SELECT name, colour FROM fruit" );
 $sth -> execute ();

 /* 从结果集中的下一行获取第一列  */
 print( "从结果集中的下一行获取第一列：\n" );
 $result  =  $sth -> fetchColumn ();
print( "name =  $result \n" );

print( "从结果集中的下一行获取第二列：\n" );
 $result  =  $sth -> fetchColumn ( 1 );
print( "colour =  $result \n" );

```
输出
```
从结果集中的下一行获取第一列：
name = lemon
从结果集中的下一行获取第二列：
colour = red

```
