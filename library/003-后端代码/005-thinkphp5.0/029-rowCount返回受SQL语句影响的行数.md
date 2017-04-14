# rowCount() 返回受SQL语句影响的行数
int PDOStatement::rowCount  ( void )
PDOStatement::rowCount() 返回上一个由对应的 PDOStatement 对象执行DELETE、 INSERT、或 UPDATE 语句受影响的行数。

如果上一条由相关 PDOStatement 执行的 SQL 语句是一条 SELECT 语句，有些数据可能返回由此语句返回的行数。但这种方式不能保证对所有数据有效，且对于可移植的应用不应依赖于此方式。
```
;返回删除的行数
/*  从 FRUIT 数据表中删除所有行 */
 $del  =  $dbh -> prepare ( 'DELETE FROM fruit' );
 $del -> execute ();

 /*  返回被删除的行数 */
 print( "Return number of rows that were deleted:\n" );
 $count  =  $del -> rowCount ();

```
输出
```
Return number of rows that were deleted:
Deleted 9 rows.

```
```
;返回select语句返回的行数

$sql  =  "SELECT COUNT(*) FROM fruit WHERE calories > 100" ;
if ( $res  =  $conn -> query ( $sql )) {

     /* 检查符合 SELECT 语句的行数 */
   if ( $res -> fetchColumn () >  0 ) {

         /* 发出一条真正的 SELECT 语句并操作返回的结果 */
          $sql  =  "SELECT name FROM fruit WHERE calories > 100" ;
       foreach ( $conn -> query ( $sql ) as  $row ) {
           print  "Name: "  .   $row [ 'NAME' ] .  "\n" ;
         }
    }
     /* 没有匹配的行 -- 执行其他 */
   else {
      print  "No rows matched the query." ;
    }
}

 $res  =  null ;
 $conn  =  null ;

```
输出
```
apple
banana
orange
pear

```
