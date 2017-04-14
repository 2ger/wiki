# bindValue() 绑定一个值到一个参数
bool PDOStatement::bindValue  ( mixed  $parameter  , mixed  $value  [, int $data_type  = PDO::PARAM_STR  ] )
$parameter:参数标识符 命名占位符:name。问号占位符使用以1为开始索引的参数位置

$value:绑定到参数的值

$data_type 指定参数的类型

PDOStatement::bindValue() ，此变量作为引用被绑定，并只在 PDOStatement::execute() 被调用的时候才取其值
```

/* 通过绑定的 PHP 变量执行一条预处理语句 */

 $calories  =  150 ;
 $colour  =  'red' ;
 $sth  =  $dbh -> prepare ( 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < :calories AND colour = :colour' );
 $sth -> bindValue ( ':calories' ,  $calories ,  PDO :: PARAM_INT );
 $sth -> bindValue ( ':colour' ,  $colour ,  PDO :: PARAM_STR );
 $sth -> execute ();

```
```
/* 通过绑定的 PHP 变量执行一条预处理语句 */

 $calories  =  150 ;
 $colour  =  'red' ;
 $sth  =  $dbh -> prepare ( 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < ? AND colour = ?' );
 $sth -> bindValue ( 1 ,  $calories ,  PDO :: PARAM_INT );
 $sth -> bindValue ( 2 ,  $colour ,  PDO :: PARAM_STR );

```
