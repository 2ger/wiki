# pdo_update
更新指定的数据表的记录

$glue 参数指定前面 $condition 数组条件的关联字 AND 或是 OR
array | boolean pdo_update($tablename, $data = array(), $condition, $glue = 'AND')
```
//更uid等于2的用户的用户名
$user_data = array(
    'username' => 'mizhou2',
);
$result = pdo_update('users', $user_data, array('id' => 2));
if (!empty($result)) {
    message('更新成功');
}

```
