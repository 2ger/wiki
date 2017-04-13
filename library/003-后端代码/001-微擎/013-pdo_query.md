# pdo_query
运行一条SQL语句

$params 指定SQL语句中绑定参数的值，参数占位与 pdo_fetch 一致
int | boolean query($sql, $params = array())
```
//更uid等于2的用户的用户名
$result = pdo_query("UPDATE ".tablename('users')." SET username = :username, age = :age WHERE uid = :uid", array(':username' => 'mizhou2', ':age' => 18, ':uid' => 2));

//删除用户名为mizhou2的记录
$result = pdo_query("DELETE FROM ".tablename('users')." WHERE uid = :uid", array(':uid' => 2));
if (!empty($result)) {
    message('删除成功');
}

```
