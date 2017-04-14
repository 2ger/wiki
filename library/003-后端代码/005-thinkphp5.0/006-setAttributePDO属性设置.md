# setAttribute() PDO属性设置
bool PDO::setAttribute  ( int $attribute  , mixed  $value  )
常见可设置数据库属性

$attribute PDO::ATTR_CASE

强制列名为指定的大小写。
PDO::CASE_LOWER：强制列名小写
PDO::CASE_UPPER：强制列名大写。
PDO::CASE_NATURAL：保留数据库驱动返回的列名
$attribute PDO::ATTR_ERRMODE

错误报告
PDO::ERRMODE_SILENT: 仅仅设置错误代码
PDO::ERRMODE_WARNING: 引发警告信息
PDO::ERRMODE_EXCEPTION: 抛出异常
$attribue PDO::ATTR_ORACLE_NULLS

空字符串和NULL的转换
PDO::NULL_NATURAL: 不转换
PDO::NULL_EMPTY_STRING：空字符串转换为NULL
PDO::NULL_TO_STRING：NULL转换为空字符串
$attribute PDO::ATTR_STRINGIFY_FETCHES

是否将数字值转换为字符串
true
false
$attribute PDO::ATTR_STATEMENT_CLASS

设置从PDOStatement派生的用户提供的语句类，
使用array(string 类名,array(mixed 构造函数的参数))
$attribue PDO::ATTR_TIMEOUT

设置超时的秒数。
$attribute PDO::ATTR_AUTOCOMMIT

设置是否自动提交每个单独的语句
$attribue PDO::ATTR_EMULATE_PREPARES

开启或关闭预处理语句的模拟
true 强制PDO使用模拟预处理语句
false 本地预处理语句
$attribute PDO::MYSQL_ATTR_USE_BUFFERED_QUERY

是否使用缓冲查询
Mysql中可以使用
$attribute PDO::ATTR_DEFAULT_FETCH_MODE

返回结果的模式
作为PDOStatement::fetch()默认值
设置数据库连接属性
