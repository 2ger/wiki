# pdo_fieldexists
检查表中是否存在某个字段

$tablename 参数指定要检查的表名称
$fieldname 参数指定要检查是否存在的字段名
boolean pdo_fieldexists($tablename, $fieldname)
```
//如果shopping_goods表中不存在credit字段，则新增credit字段
if(!pdo_fieldexists('shopping_goods', 'credit')) {
    pdo_query("ALTER TABLE ".tablename('shopping_goods')." ADD `credit` int(11) NOT NULL DEFAULT '0';");
}

```
