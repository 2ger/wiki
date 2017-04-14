# fetch() 从结果集中获取下一行
mixed  PDOStatement::fetch  ([ int $fetch_style  [, int $cursor_orientation  = PDO::FETCH_ORI_NEXT  [, int $cursor_offset  = 0  ]]] )
$fetch_style

控制下一行如何返回给调用者。此值必须是 PDO::FETCH_* 系列常量中的一个，缺省为 PDO::ATTR_DEFAULT_FETCH_MODE 的值 （默认为 PDO::FETCH_BOTH ）。

PDO::FETCH_ASSOC：返回一个索引为结果集列名的数组

PDO::FETCH_BOTH（默认）：返回一个索引为结果集列名和以0开始的列号的数组

PDO::FETCH_BOUND：返回 TRUE ，并分配结果集中的列值给 PDOStatement::bindColumn() 方法绑定的 PHP 变量。

PDO::FETCH_CLASS：返回一个请求类的新实例，映射结果集中的列名到类中对应的属性名。如果 fetch_style 包含 PDO::FETCH_CLASSTYPE（例如：PDO::FETCH_CLASS | PDO::FETCH_CLASSTYPE），则类名由第一列的值决定

PDO::FETCH_INTO：更新一个被请求类已存在的实例，映射结果集中的列到类中命名的属性

PDO::FETCH_LAZY：结合使用 PDO::FETCH_BOTH 和 PDO::FETCH_OBJ，创建供用来访问的对象变量名

PDO::FETCH_NUM：返回一个索引为以0开始的结果集列号的数组

PDO::FETCH_OBJ：返回一个属性名对应结果集列名的匿名对象

$cursor_orientation

对于 一个 PDOStatement 对象表示的可滚动游标，该值决定了哪一行将被返回给调用者。此值必须是 PDO::FETCH_ORI_* 系列常量中的一个，默认为 PDO::FETCH_ORI_NEXT。要想让 PDOStatement 对象使用可滚动游标，必须在用 PDO::prepare() 预处理SQL语句时，设置 PDO::ATTR_CURSOR 属性为 PDO::CURSOR_SCROLL。
$offset

对于一个 cursor_orientation 参数设置为 PDO::FETCH_ORI_ABS 的PDOStatement 对象代表的可滚动游标，此值指定结果集中想要获取行的绝对行号。

对于一个 cursor_orientation 参数设置为 PDO::FETCH_ORI_REL 的PDOStatement 对象代表的可滚动游标，此值指定想要获取行相对于调用 PDOStatement::fetch() 前游标的位置
从PDOStatement::execute()执行预处理语句的结果集中获取下一行。返回值依赖于PDO中PDO::FETCH_* 的配置

Eg1: 使用不同的提取方式获取行
```
$sth  =  $dbh -> prepare ( "SELECT name, colour FROM fruit" );
 $sth -> execute ();

 /* 运用 PDOStatement::fetch 风格 */
 print( "PDO::FETCH_ASSOC: " );
print( "Return next row as an array indexed by column name\n" );
 $result  =  $sth -> fetch ( PDO :: FETCH_ASSOC );
 print_r ( $result );
print( "\n" );

print( "PDO::FETCH_BOTH: " );
print( "Return next row as an array indexed by both column name and number\n" );
 $result  =  $sth -> fetch ( PDO :: FETCH_BOTH );
 print_r ( $result );
print( "\n" );

print( "PDO::FETCH_LAZY: " );
print( "Return next row as an anonymous object with column names as properties\n" );
 $result  =  $sth -> fetch ( PDO :: FETCH_LAZY );
 print_r ( $result );
print( "\n" );

print( "PDO::FETCH_OBJ: " );
print( "Return next row as an anonymous object with column names as properties\n" );
 $result  =  $sth -> fetch ( PDO :: FETCH_OBJ );
print  $result -> NAME ;
print( "\n" );

```
输出
```
PDO::FETCH_ASSOC: Return next row as an array indexed by column name
Array
(
    [NAME] => apple
    [COLOUR] => red
)PDO::FETCH_BOTH: Return next row as an array indexed by both column name and number
Array
(
    [NAME] => banana
    [0] => banana
    [COLOUR] => yellow
    [1] => yellow
)PDO::FETCH_LAZY: Return next row as an anonymous object with column names as properties
PDORow Object
(
    [NAME] => orange
    [COLOUR] => orange
)PDO::FETCH_OBJ: Return next row as an anonymous object with column names as properties
kiwi

```
Eg2:使用可滚动游标获取行

```
function  readDataForwards ( $dbh ) {
   $sql  =  'SELECT hand, won, bet FROM mynumbers ORDER BY BET' ;
  try {
     $stmt  =  $dbh -> prepare ( $sql , array( PDO :: ATTR_CURSOR  =>  PDO :: CURSOR_SCROLL ));
     $stmt -> execute ();
    while ( $row  =  $stmt -> fetch ( PDO :: FETCH_NUM ,  PDO :: FETCH_ORI_NEXT )) {
       $data  =  $row [ 0 ] .  "\t"  .  $row [ 1 ] .  "\t"  .  $row [ 2 ] .  "\n" ;
      print  $data ;
    }
     $stmt  =  null ;
  }
  catch ( PDOException $e ) {
    print  $e -> getMessage ();
  }
}
function  readDataBackwards ( $dbh ) {
   $sql  =  'SELECT hand, won, bet FROM mynumbers ORDER BY bet' ;
  try {
     $stmt  =  $dbh -> prepare ( $sql , array( PDO :: ATTR_CURSOR  =>  PDO :: CURSOR_SCROLL ));
     $stmt -> execute ();
     $row  =  $stmt -> fetch ( PDO :: FETCH_NUM ,  PDO :: FETCH_ORI_LAST );
    do {
       $data  =  $row [ 0 ] .  "\t"  .  $row [ 1 ] .  "\t"  .  $row [ 2 ] .  "\n" ;
      print  $data ;
    } while ( $row  =  $stmt -> fetch ( PDO :: FETCH_NUM ,  PDO :: FETCH_ORI_PRIOR ));
     $stmt  =  null ;
  }
  catch ( PDOException $e ) {
    print  $e -> getMessage ();
  }
}

print  "Reading forwards:\n" ;
 readDataForwards ( $conn );

print  "Reading backwards:\n" ;
 readDataBackwards ( $conn );

```
输出
```
Reading forwards:
21    10    5
16    0     5
19    20    10Reading backwards:
19    20    10
16    0     5
21    10    5

```
