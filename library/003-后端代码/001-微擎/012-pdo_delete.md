
# pdo_delete
删除指定条件的数据

int | boolean pdo_delete($tablename, $condition = array(), $glue = 'AND')
```
//删除用户名为mizhou2的记录
$result = pdo_delete('users', array('username' => 'mizhou2'));
if (!empty($result)) {
    message('删除成功');
}

```
