
# pdo_insert
对指定数据表插入一条新记录

$tablename 参数指定要插入记录的数据表名，此处传入的表名不要使用tablename()函数
$data 参数指定要插入的记录，格式为与数据表字段对应的关联数组
$replace 参数指定插入方式使用 INSERT 语句或是 REPLACE 语句(查找到主键相同的数据选择update)
int | boolean pdo_insert($tablename, $data = array(), $replace = false)
```
//添加一条用户记录，并判断是否成功
$user_data = array(
    'username' => 'mizhou1',
    'status' => '1',
);
$result = pdo_insert('users', $user_data);
if (!empty($result)) {
    $uid = pdo_insertid();
    message('添加用户成功，UID为' . $uid);
}

```
