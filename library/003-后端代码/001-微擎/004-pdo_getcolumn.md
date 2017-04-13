# pdo_getcolumn
根据条件（AND连接）到指定的表中获取一条记录的指定字段

$tablename 参数指定要查询的数据表名，此处传入的表名不要使用tablename()函数
$condition 参数指定查询的条件，以是 AND 连接，支持大于，小于等范围条件.。具体使用查看本章节第二段范围条件操作
$field 参数指定查询返回的字段
$limit 参数指定查询表中获取一条记录
string | int pdo_getcolumn($tablename, $condition = array(), $field, $limit=1);
```
//根据uid获取用户的用户名
//生成的SQL等同于：SELECT username FROM ims_users WHERE uid = '1' LIMIT 1
$username = pdo_getcolumn('users', array('uid' => 1), 'username',1);

```
