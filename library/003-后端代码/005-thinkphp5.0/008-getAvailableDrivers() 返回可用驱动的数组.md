# getAvailableDrivers() 返回可用驱动的数组
static array PDO::getAvailableDrivers  ( void )
返回在PDO::__construct()参数DSN中的PDO可以驱动类型
print_r ( PDO :: getAvailableDrivers ());
输出:
```
Array
(
    [0] => mysql
    [1] => sqlite
)

```
