# getAttribute() PDO属性获取
mixed  PDO::getAttribute  ( int $attribute  )
$attribute 返回数据库连接属性，下列属性的一个

PDO::ATTR_AUTOCOMMIT
PDO::ATTR_CASE
PDO::ATTR_CLIENT_VERSION
PDO::ATTR_CONNECTION_STATUS
PDO::ATTR_DRIVER_NAME
PDO::ATTR_ERRMODE
PDO::ATTR_ORACLE_NULLS
PDO::ATTR_PERSISTENT
PDO::ATTR_PREFETCH
PDO::ATTR_SERVER_INFO
PDO::ATTR_SERVER_VERSION
PDO::ATTR_TIMEOUT
成功调用返回请求的PDO属性值，不成功返回null
```

$conn  = new  PDO ( 'odbc:sample' ,  'db2inst1' ,  'ibmdb2' );
 $attributes  = array(
     "AUTOCOMMIT" ,  "ERRMODE" ,  "CASE" ,  "CLIENT_VERSION" ,  "CONNECTION_STATUS" ,
     "ORACLE_NULLS" ,  "PERSISTENT" ,  "PREFETCH" ,  "SERVER_INFO" ,  "SERVER_VERSION" ,
     "TIMEOUT"
 );

foreach ( $attributes  as  $val ) {
    echo  "PDO::ATTR_ $val : " ;
    echo  $conn -> getAttribute ( constant ( "PDO::ATTR_ $val " )) .  "\n" ;
}

```
