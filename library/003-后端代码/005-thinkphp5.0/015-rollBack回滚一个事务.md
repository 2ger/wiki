# rollBack() 回滚一个事务
回滚由PDO::beginTransaction()  发起的当前事务中的手动提交

设置成自动提交模式，的回滚事务后恢复自动提交模式

包括 MySQL 在内的一些数据库， 当在一个事务内有类似删除或创建数据表等 DLL 语句时，会自动导致一个隐式地提交。隐式地提交将无法回滚此事务范围内的任何更改
```
;在 MySQL 中，DROP TABLE 语句自动提交事务，因此在此事务内的任何更改都不会被回滚。

/* 开始一个事务，关闭自动提交 */
 $dbh -> beginTransaction ();

 /* 更改数据库架构和数据  */
 $sth  =  $dbh -> exec ( "DROP TABLE fruit" );
 $sth  =  $dbh -> exec ( "UPDATE dessert
    SET name = 'hamburger'" );

 /*  识别错误且回滚更改  */
 $dbh -> rollBack ();

 /*  此时数据库连接恢复到自动提交模式  */

```
