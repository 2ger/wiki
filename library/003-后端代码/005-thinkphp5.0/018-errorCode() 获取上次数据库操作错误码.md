# errorCode() 获取上次数据库操作错误码
```
mixed  PDO::errorCode  ( void )

```
返回一个SQLSTATE说明码，一个由5个字母或数字组成的SQL标准定义的标识符
```
$dbh -> exec ( "INSERT INTO bones(skull) VALUES ('lucy')" );

echo  "\nPDO::errorCode(): " ;
print  $dbh -> errorCode ();

```
输出
```

PDO::errorCode(): 42S02


```
