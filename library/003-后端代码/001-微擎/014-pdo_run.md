# pdo_run
批量执行SQL语句

$stuff 函数将会将此参数指定的值，替换为当前系统的表前缀。
注：与pdo_query不同的是，pdo_run是可以一次执行多条SQL语句，每条SQL必须以;分隔。
boolean run($sql, $stuff = 'ims_')
```
$sql = <<<EOF
CREATE TABLE IF NOT EXISTS `ims_multisearch` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `weid` int(10) unsigned NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM  DEFAULT CHARSET=utf8;

CREATE TABLE IF NOT EXISTS `ims_multisearch_fields` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `reid` int(10) unsigned NOT NULL,
  `type` tinyint(1) unsigned NOT NULL DEFAULT '1',
  `title` varchar(255) NOT NULL,
  PRIMARY KEY (`id`),
  KEY `idx_reid` (`reid`)
) ENGINE=MyISAM  DEFAULT CHARSET=utf8;
EOF;

pdo_run($sql);

```
