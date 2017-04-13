# pdo_getslice
根据条件（AND连接）到指定的表中获取某个区间的记录，此函数和 pdo_getall 的区别是可以指定limit 值

$condition 参数指定查询的条件，以是 AND 连接，支持大于，小于等范围条件.。具体使用查看本章节第二段范围条件操作
$limit 参数指定查询语句的LIMIT值，array(start, end) 或是直接传入范围 2,3
$total 参数指定查询结果的总条数，方便进行分页操作
$orderby 参数指定查询结果按哪个字段排序
array | boolean pdo_getslice($tablename, $condition = array(), $limit = array(), &$total = null, $fields = array(), $keyfie
```
//获取从第一条数据开始的10条启用的用户
//生成的SQL等同于$user = SELECT * FROM  ims_users WHERE status ='2' ORDER BY uid,groupid LIMIT 0, 10
$user = pdo_getslice('users', array('status' => 2), array(1,10) , $total , array() , '' , array('uid','groupid'));

```
