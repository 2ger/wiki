
tablename()

为了防止微擎系统的表与其它系统命名冲突，安装微擎时均会指定一个表前缀，在写SQL语句时，需要将表名称附加上表前缀。可以使用 tablename() 函数。

```
$sql = "SELECT * FROM ".tablename('users');
echo $sql;

//输出 SELECT * FROM ims_users

```
