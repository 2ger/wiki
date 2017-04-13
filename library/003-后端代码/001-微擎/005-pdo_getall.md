# pdo_getall
根据条件（AND连接）到指定的表中获取全部记录

$condition 参数指定查询的条件，以是 AND 连接，支持大于，小于等范围条件.。具体使用查看本章节第二段范围条件操作
$keyfield 参数传入一个已存在的字段名称，结果数组键值就为该字段，否则为自然排序
$orderby 参数指定查询结果按哪个字段排序
$limit 参数指定查询语句的LIMIT值，array(start, end) 或是直接传入范围 2,3
其它参数同pdo_get函数
array | boolean pdo_getall($tablename, $condition = array(), $fields = array(), $keyfield = '',$orderby = array(), $limit = a
```
//获取全部启用的用户
//生成的SQL等同于：SELECT * FROM ims_users WHERE status = '1'
$user = pdo_getall('users', array('status' => 1));
//获取从第一条数据开始的10条启用的用户
//生成的SQL等同于：SELECT * FROM ims_users WHERE status =' 2' ORDER BY uid,groupid LIMIT 0, 10
$user = pdo_getall('users', array('status' => 1), array() , '' , array('uid','groupid') , array(1,10));

$user1 = pdo_getall('users', array('status' => 1), array() , '' , 'uid DESC' , array(1,10));

```
