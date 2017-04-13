# pdo_fetch
根据SQL语句，查询一条记录

$sql 参数指定要返回记录集的SQL语句
$params 参数指定为SQL语句中的参数绑定传值，防止SQL注入
需要注意的是使用参数绑定时，SQL语中等号后不需要使用引号，传入的值必须与绑定的名称一致
array | boolean pdo_fetch($sql, $params = array());

```
// :uid 是参数的一个占位符，没有使用引号，传入的第二个参数中要与SQL中的占位名称相同
$user = pdo_fetch("SELECT username, uid FROM ".tablename('users')." WHERE uid = :uid LIMIT 1", array(':uid' => 1));
// LIKE 占位的使用方法
$user = pdo_fetch("SELECT * FROM ".tablename('users')." WHERE username LIKE :username", array(':username' => '%mizhou%'));

```
