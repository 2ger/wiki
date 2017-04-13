# pdo_indexexists
检查表中是否存在某个索引

$tablename 参数指定要检查的表名称
$indexname 参数指定要检查是否存在的索引名
boolean pdo_indexexists($tablename, $indexname)
```
//如果site_slide表中不存在multiid索引，则新增multiid索引
if (!pdo_indexexists('site_slide', 'multiid')) {
    pdo_query("ALTER TABLE ".tablename('site_slide')." ADD INDEX `multiid` (`multiid`);");
}

```
