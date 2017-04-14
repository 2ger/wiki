# lastInsertId() 返回最后插入行的ID或序列值
string PDO::lastInsertId  ([ string $name  = NULL    ] )
返回ID对应的序列对象的名称

如果没有为参数 name 指定序列名称， PDO::lastInsertId() 则返回一个表示最后插入数据库那一行的行ID的字符串。

如果为参数 name 指定了序列名称， PDO::lastInsertId() 则返回一个表示从指定序列对象取回最后的值的字符串。

如果当前 PDO 驱动不支持此功能，则 PDO::lastInsertId() 触发一个 IM001 SQLSTATE 。
