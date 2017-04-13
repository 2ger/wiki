# pdo_fetchall
根据SQL语句，查询全部记录，使用方法与pdo_fetch相同

array | boolean pdo_fetchall($sql, $params = array(), $keyfield = '')
```
// 需要注意的是，返回的数组的键值为用户的uid
$user = pdo_fetchall("SELECT username, uid FROM ".tablename('users'), array(), 'uid');

```
