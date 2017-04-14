# prepare() 准备待执行SQL语句
public PDOStatement  PDO::prepare  ( string $statement  [, array $driver_options  = array()  ] )
$statement:sql语句
$driver_options:数据库驱动参数
返回待执行的PDOStatement对象

```
$sql  =  'SELECT name, colour, calories
    FROM fruit
    WHERE calories < :calories AND colour = :colour' ;
 $sth  =  $dbh -> prepare ( $sql , array( PDO :: ATTR_CURSOR  =>  PDO :: CURSOR_FWDONLY ));
 $sth -> execute (array( ':calories'  =>  150 ,  ':colour'  =>  'red' ));
 $red  =  $sth -> fetchAll ();
 $sth -> execute (array( ':calories'  =>  175 ,  ':colour'  =>  'yellow' ));
 $yellow  =  $sth -> fetchAll ();

```
```
;?占位符sql语句生成

$sth  =  $dbh -> prepare ( 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < ? AND colour = ?' );
 $sth -> execute (array( 150 ,  'red' ));
 $red  =  $sth -> fetchAll ();
 $sth -> execute (array( 175 ,  'yellow' ));
 $yellow  =  $sth -> fetchAll ();

```
