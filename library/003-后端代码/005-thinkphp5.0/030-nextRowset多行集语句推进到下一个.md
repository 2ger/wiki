# nextRowset() 在一个多行集语句句柄中推进到下一个行集
bool PDOStatement::nextRowset  ( void )
一些数据库服务支持返回一个以上行集（也被称为结果集）的存储过程。 PDOStatement::nextRowset() 使你能够结合一个 PDOStatement 对象访问第二个以及后续的行集。上述的每个行集可以有不同的列集合。
```
;获取一个存储过程返回的多个行集

$sql  =  'CALL multiple_rowsets()' ;
 $stmt  =  $conn -> query ( $sql );
 $i  =  1 ;
do {
     $rowset  =  $stmt -> fetchAll ( PDO :: FETCH_NUM );
    if ( $rowset ) {
         printResultSet ( $rowset ,  $i );
    }
     $i ++;
} while ( $stmt -> nextRowset ());

function  printResultSet (& $rowset ,  $i ) {
    print  "Result set  $i :\n" ;
    foreach ( $rowset  as  $row ) {
        foreach ( $row  as  $col ) {
            print  $col  .  "\t" ;
        }
        print  "\n" ;
    }
    print  "\n" ;
}

```
输出
```

Result set 1:
apple    red
banana   yellowResult set 2:
orange   orange    150
banana   yellow    175Result set 3:
lime     green
apple    red
banana   yellow
```
