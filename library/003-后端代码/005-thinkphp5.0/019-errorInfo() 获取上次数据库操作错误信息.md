# errorInfo() 获取上次数据库操作错误信息
public array PDO::errorInfo  ( void )
返回错误信息数组

SQLSTATE
Driver error code
Driver error message
$stmt  =  $dbh -> prepare ( 'bogus sql' );
if (! $stmt ) {
    echo  "\nPDO::errorInfo():\n" ;
     print_r ( $dbh -> errorInfo ());
}
输出
```

PDO::errorInfo():
Array
(
    [0] => HY000
    [1] => 1
    [2] => near "bogus": syntax error
)

```
