# fetchAll() 返回结果集中所有行的数组
array PDOStatement::fetchAll  ([ int $fetch_style  [, mixed  $fetch_argument  [, array $ctor_args  = array()  ]]] )
$fetch_style 结果集类型

$fetch_argument 结果列参数

PDO::FETCH_COLUMN ：返回指定以0开始索引的列。

PDO::FETCH_CLASS ：返回指定类的实例，映射每行的列到类中对应的属性名。

PDO::FETCH_FUNC ：将每行的列作为参数传递给指定的函数，并返回调用函数后的结果。
　$ctor_args 自定义类的构造函数的参数。

当 fetch_style 参数为 PDO::FETCH_CLASS 时，自定义类的构造函数的参数。
返回包含结果集中所有剩余行的数组。此数组的每一行要么是一个列值的数组，要么是属性对应每个列名的一个对象。

使用此方法获取大结果集将导致系统负担加重且可能占用大量网络资源。与其取回所有数据后用PHP来操作，倒不如考虑使用数据库服务来处理结果集。例如，在取回数据并通过PHP处理前，在 SQL 中使用 WHERE 和 ORDER BY 子句来限定结果。
```
;获取结果集中所有剩余的行
$sth  =  $dbh -> prepare ( "SELECT name, colour FROM fruit" );
 $sth -> execute ();

 /* 获取结果集中所有剩余的行 */
 print( "Fetch all of the remaining rows in the result set:\n" );
 $result  =  $sth -> fetchAll ();
 print_r ( $result );

```
输出
```
Fetch all of the remaining rows in the result set:
Array
(
    [0] => Array
        (
            [NAME] => pear
            [0] => pear
            [COLOUR] => green
            [1] => green
        )    [1] => Array
        (
            [NAME] => watermelon
            [0] => watermelon
            [COLOUR] => pink
            [1] => pink
        ))

```
```
;获取结果集中单独一列的所有值

$sth  =  $dbh -> prepare ( "SELECT name, colour FROM fruit" );
 $sth -> execute ();

 /* 获取第一列所有值 */
 $result  =  $sth -> fetchAll ( PDO :: FETCH_COLUMN ,  0 );
 var_dump ( $result );

```
```
Array(3)
(
    [0] =>
    string(5) => apple
    [1] =>
    string(4) => pear
    [2] =>
    string(10) => watermelon
)

```
```
;根据单独的一列把所有值分组

$insert  =  $dbh -> prepare ( "INSERT INTO fruit(name, colour) VALUES (?, ?)" );
 $insert -> execute (array( 'apple' ,  'green' ));
 $insert -> execute (array( 'pear' ,  'yellow' ));

 $sth  =  $dbh -> prepare ( "SELECT name, colour FROM fruit" );
 $sth -> execute ();

 /* 根据第一列分组  */
 var_dump ( $sth -> fetchAll ( PDO :: FETCH_COLUMN | PDO :: FETCH_GROUP ));

```
输出
```
array(3) {
  ["apple"]=>
  array(2) {
    [0]=>
    string(5) "green"
    [1]=>
    string(3) "red"
  }
  ["pear"]=>
  array(2) {
    [0]=>
    string(5) "green"
    [1]=>
    string(6) "yellow"
  }
  ["watermelon"]=>
  array(1) {
    [0]=>
    string(5) "green"
  }
}

```
```
;返回每行结果实例化为一个类

class  fruit  {
    public  $name ;
    public  $colour ;
}

 $sth  =  $dbh -> prepare ( "SELECT name, colour FROM fruit" );
 $sth -> execute ();

 $result  =  $sth -> fetchAll ( PDO :: FETCH_CLASS ,  "fruit" );
 var_dump ( $result );

```
输出
```
array(3) {
  [0]=>
  object(fruit)#1 (2) {
    ["name"]=>
    string(5) "apple"
    ["colour"]=>
    string(5) "green"
  }
  [1]=>
  object(fruit)#2 (2) {
    ["name"]=>
    string(4) "pear"
    ["colour"]=>
    string(6) "yellow"
  }
  [2]=>
  object(fruit)#3 (2) {
    ["name"]=>
    string(10) "watermelon"
    ["colour"]=>
    string(4) "pink"
  }
}

``````


;每行调用一次函数

function  fruit ( $name ,  $colour ) {
    return  " { $name } :  { $colour } " ;
}

 $sth  =  $dbh -> prepare ( "SELECT name, colour FROM fruit" );
 $sth -> execute ();

 $result  =  $sth -> fetchAll ( PDO :: FETCH_FUNC ,  "fruit" );
 var_dump ( $result );

```
输出
```
array(3) {
  [0]=>
  string(12) "apple: green"
  [1]=>
  string(12) "pear: yellow"
  [2]=>
  string(16) "watermelon: pink"
}

```
