#  __construct()构造函数
PDO::__construct  ( string $dsn  [, string $username  [, string $password  [, array $driver_options  ]]] )
$dsn: 数据源名称或叫做DSN，包含了请求连接到数据库的信息，通常一个DSN由PDO驱动名，紧随其后的冒号以及具体的PDO驱动的连接语法组成，支持三种不同方式的DSN
$username: DSN字符串中的用户名
$password: DSN字符串中的密码
driver_options: 数据库连接键值对参数
