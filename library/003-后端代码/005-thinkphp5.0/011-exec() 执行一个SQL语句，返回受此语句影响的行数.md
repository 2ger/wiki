# exec() 执行一个SQL语句，返回受此语句影响的行数
```
int PDO::exec  ( string $statement  )

```
$statement 被预处理和执行的SQL语句
单独函数中执行一条SQL语句，返回受此语句影响的行数
```
$db -> exec () or die( print_r ( $db -> errorInfo (),  true ));

$dbh  = new  PDO ( 'odbc:sample' ,  'db2inst1' ,  'ibmdb2' );
$count  =  $dbh -> exec ( "DELETE FROM fruit WHERE colour = 'red'" );
print( "Deleted  $count  rows.\n" );

```
