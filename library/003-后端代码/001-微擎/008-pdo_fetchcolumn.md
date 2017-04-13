# pdo_fetchcolumn
根据SQL语句，查询第一条记录的第N列的值，此语句与 pdo_fetch 使用相同，只是此函数返回的不是一个数组而是一个字符串

$column 参数指定返回记录集的第几列数据
string | boolean pdo_fetchcolumn($sql, $params = array(), $column = 0)
```
// 获取用户的总数，返回的值是一个数字
$user_total = pdo_fetchcolumn("SELECT COUNT(*) FROM ".tablename('users'));

```
