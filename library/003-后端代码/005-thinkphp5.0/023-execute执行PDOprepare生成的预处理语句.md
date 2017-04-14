# execute() 执行PDO::prepare()生成的预处理语句
bool PDOStatement::execute  ([ array $input_parameters  ] )
$input_parameters:绑定参数列表

1.调用 PDOStatement::bindParam() 绑定 PHP 变量到参数标记：如果有的话，通过关联参数标记绑定的变量来传递输入值和取得输出值

2.或传递一个只作为输入参数值的数组
```
;绑定变量到预处理语句并执行
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
/* 通过传递一个含有插入值的数组执行一条预处理语句 */
 $calories  =  150 ;
 $colour  =  'red' ;
 $sth  =  $dbh -> prepare ( 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < :calories AND colour = :colour' );
 $sth -> execute (array( ':calories'  =>  $calories ,  ':colour'  =>  $colour /*

```
```
;通过传递一个含有插入值的数组执行一条预处理语句 */
 $calories  =  150 ;
 $colour  =  'red' ;
 $sth  =  $dbh -> prepare ( 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < :calories AND colour = :colour' );
 $sth -> execute (array( ':calories'  =>  $calories ,  ':colour'  =>  $colour ));));

```
