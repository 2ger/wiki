# bindParam() 绑定参数到预处理语句
bool PDOStatement::bindParam  ( mixed  $parameter  , mixed  &$variable  [, int $data_type  = PDO::PARAM_STR  [, int $length  [, mixed  $driver_options  ]]] )
$paramter 参数标识符 命名占位符:name。问号占位符使用以1为开始索引的参数位置

$varibale 绑定到参数的变量名

$data_type 指定参数的类型

$length 数据类型的长度

$driver_options 驱动配置参数

绑定一个PHP变量到用作预处理的SQL语句中的对应命名占位符或问号占位符。 不同于 PDOStatement::bindValue() ，此变量作为引用被绑定，并只在 PDOStatement::execute() 被调用的时候才取其值。

大多数参数是输入参数，即，参数以只读的方式用来建立查询。一些驱动支持调用存储过程并作为输出参数返回数据，一些支持作为输入/输出参数，既发送数据又接收更新后的数据。
```
/* 通过绑定的 PHP 变量执行一条预处理语句  */
 $calories  =  150 ;
 $colour  =  'red' ;
 $sth  =  $dbh -> prepare ( 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < :calories AND colour = :colour' );
 $sth -> bindParam ( ':calories' ,  $calories ,  PDO :: PARAM_INT );
 $sth -> bindParam ( ':colour' ,  $colour ,  PDO :: PARAM_STR ,  12 );
 $sth -> execute ();

```
```
/*  通过绑定的 PHP 变量执行一条预处理语句 */
$calories  =  150 ;
 $colour  =  'red' ;
 $sth  =  $dbh -> prepare ( 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < ? AND colour = ?' );
 $sth -> bindParam ( 1 ,  $calories ,  PDO :: PARAM_INT );
 $sth -> bindParam ( 2 ,  $colour ,  PDO :: PARAM_STR ,  12 );
 $sth -> execute ();

```
```
/* 使用 INOUT 参数调用一个存储过程 */

 $colour  =  'red' ;
 $sth  =  $dbh -> prepare ( 'CALL puree_fruit(?)' );
 $sth -> bindParam ( 1 ,  $colour ,  PDO :: PARAM_STR | PDO :: PARAM_INPUT_OUTPUT ,  12 );
 $sth -> execute ();
print( "After pureeing fruit, the colour is:  $colour " );

```
