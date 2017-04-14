# query() 执行SQL语句，返回PDOStatement对象
```
public PDOStatement  PDO::query  ( string $statement  )

public PDOStatement  PDO::query  ( string $statement  , int $PDO::FETCH_COLUMN  , int $colno  )

public PDOStatement  PDO::query  ( string $statement  , int $PDO::FETCH_CLASS  , string $classname  , array $ctorargs  )

public PDOStatement  PDO::query  ( string $statement  , int $PDO::FETCH_INTO  , object $object  )

```
$statement:待执行sql语句
```
function  getFruit ( $conn ) {
     $sql  =  'SELECT name, color, calories FROM fruit ORDER BY name' ;
    foreach ( $conn -> query ( $sql ) as  $row ) {
        print  $row [ 'name' ] .  "\t" ;
        print  $row [ 'color' ] .  "\t" ;
        print  $row [ 'calories' ] .  "\n" ;
    }
}

```
输出

```
apple   red     150
banana  yellow  250
kiwi    brown   75
lemon   yellow  25
orange  orange  300
pear    green   150
watermelon      pink    90

```
