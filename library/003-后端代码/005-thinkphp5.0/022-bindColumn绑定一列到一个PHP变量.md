# bindColumn() 绑定一列到一个PHP变量
bool PDOStatement::bindColumn  ( mixed  $column  , mixed  &$param  [, int $type  [, int $maxlen  [, mixed  $driverdata  ]]] )
$column 结果集中的列号（从1开始索引）或列名。如果使用列名，注意名称应该与由驱动返回的列名大小写保持一致。

$param 将绑定到列的 PHP 变量名称

$type 通过 PDO::PARAM_* 常量指定的参数的数据类型。

$maxlen 预分配提示。

$driverdata 驱动的可选参数。
```
;结果集输出绑定到PHP变量

function  readData ( $dbh ) {
   $sql  =  'SELECT name, colour, calories FROM fruit' ;
  try {
     $stmt  =  $dbh -> prepare ( $sql );
     $stmt -> execute ();

     /*  通过列号绑定  */
     $stmt -> bindColumn ( 1 ,  $name );
     $stmt -> bindColumn ( 2 ,  $colour );

     /*  通过列名绑定  */
     $stmt -> bindColumn ( 'calories' ,  $cals );

    while ( $row  =  $stmt -> fetch ( PDO :: FETCH_BOUND )) {
       $data  =  $name  .  "\t"  .  $colour  .  "\t"  .  $cals  .  "\n" ;
      print  $data ;
    }
  }
  catch ( PDOException $e ) {
    print  $e -> getMessage ();
  }
}
 readData ( $dbh );

```
输出
```
apple   red     150
banana  yellow  175
kiwi    green   75
orange  orange  150
mango   red     200
strawberry      red     25

```
