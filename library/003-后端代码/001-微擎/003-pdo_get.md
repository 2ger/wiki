# pdo_get
根据条件（AND连接）到指定的表中获取一条记录

$tablename 参数指定要查询的数据表名，此处传入的表名不要使用tablename()函数
$condition 参数指定查询的条件，以是 AND 连接，支持大于，小于等范围条件。具体使用查看本章节第二段范围条件操作
$fields 参数指定查询返回的字段列表
$limit 参数指定查询表中获取一条记录
array | boolean pdo_get($tablename, $condition = array(), $fields = array());

```
//根据uid获取用户的用户名和用户Id信息
//生成的SQL等同于：SELECT username, uid FROM ims_users WHERE uid = '1' LIMIT 1
$user = pdo_get('users', array('uid' => 1), array('username', 'uid'));

//生成的SQL等同于：SELECT username FROM ims_users WHERE username = 'mizhou' AND status = '1' LIMIT 1
$user = pdo_get('users', array('username' => 'mizhou', 'status' => 1), array('username'));

```
