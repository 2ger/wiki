# setFetchMode() 设置语句的获取模式
```
bool PDOStatement::setFetchMode  ( int $mode  )

bool PDOStatement::setFetchMode  ( int $PDO::FETCH_COLUMN  , int $colno  )

bool PDOStatement::setFetchMode  ( int $PDO::FETCH_CLASS  , string $classname  , array $ctorargs  )

bool PDOStatement::setFetchMode  ( int $PDO::FETCH_INTO  , object $object  )

```
$mode PDO::FETCH_*系列常量的一个

1 PDO::FETCH_ASSOC：返回一个索引为结果集列名的数组

2 PDO::FETCH_BOTH（默认）：返回一个索引为结果集列名和以0开始的列号的数组

3 PDO::FETCH_BOUND：返回 TRUE ，并分配结果集中的列值给 PDOStatement::bindColumn() 方法绑定的 PHP 变量。

4 PDO::FETCH_CLASS：返回一个请求类的新实例，映射结果集中的列名到类中对应的属性名。如果 fetch_style 包含 PDO::FETCH_CLASSTYPE（例如：PDO::FETCH_CLASS | PDO::FETCH_CLASSTYPE），则类名由第一列的值决定
5 PDO::FETCH_INTO：更新一个被请求类已存在的实例，映射结果集中的列到类中命名的属性

6 PDO::FETCH_LAZY：结合使用 PDO::FETCH_BOTH 和 PDO::FETCH_OBJ，创建供用来访问的对象变量名

7 PDO::FETCH_NUM：返回一个索引为以0开始的结果集列号的数组

8 PDO::FETCH_OBJ：返回一个属性名对应结果集列名的匿名对象
$colno 列号
$classname 类名
$ctorargs 构造函数参数
$object 对象
```
;设置获取模式
$sql  =  'SELECT name, colour, calories FROM fruit' ;
try {
   $stmt  =  $dbh -> query ( $sql );
   $result  =  $stmt -> setFetchMode ( PDO :: FETCH_NUM );
  while ( $row  =  $stmt -> fetch ()) {
    print  $row [ 0 ] .  "\t"  .  $row [ 1 ] .  "\t"  .  $row [ 2 ] .  "\n" ;
  }
}
catch ( PDOException $e ) {
  print  $e -> getMessage ();
}

```
输出
```
apple   red     150
banana  yellow  250
orange  orange  300
kiwi    brown   75
lemon   yellow  25
pear    green   150
watermelon      pink    90

```
