# pdo_debug
调试运行SQL语句，显示执行过的SQL的栈情况

$output 参数指定是否直接打印出调试信息
array debug($output = true, $append = array())
```
pdo_debug();

//调用该函数结果如下
Array
(
[0] => Array
    (
        [sql] => SET NAMES 'utf8';
        [error] => Array
            (
                [0] => 00000
                [1] =>
                [2] =>
            )
    )
[1] => Array
    (
        [sql] => SELECT `value` FROM `ims_core_cache` WHERE `key`=:key
        [params] => Array
            (
                [:key] => setting
            )
        [error] => Array
            (
                [0] => 00000
                [1] =>
                [2] =>
            )
    )
)

```
