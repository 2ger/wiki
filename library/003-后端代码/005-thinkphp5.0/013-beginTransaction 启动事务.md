# beginTransaction 启动事务
bool PDO::beginTransaction  ( void )
关闭自动提交，进入事务的手动提交模式
```
/* 开始一个事务，关闭自动提交 */
 $dbh -> beginTransaction ();

 /*  更改数据库架构及数据 */
 $sth  =  $dbh -> exec ( "DROP TABLE fruit" );
 $sth  =  $dbh -> exec ( "UPDATE dessert
    SET name = 'hamburger'" );

 /*  识别出错误并回滚更改 */
 $dbh -> rollBack ();

 /* 数据库连接现在返回到自动提交模式 */

```
