# commint() 手动提交事务
bool PDO::commit  ( void )
事务中进行手动提交，返回到自动提交模式
```

/* 开始一个事务，关闭自动提交 */
 $dbh -> beginTransaction ();

 /* 在全有或全无的基础上插入多行记录（要么全部插入，要么全部不插入） */
 $sql  =  'INSERT INTO fruit
    (name, colour, calories)
    VALUES (?, ?, ?)' ;

 $sth  =  $dbh -> prepare ( $sql );

foreach ( $fruits  as  $fruit ) {
     $sth -> execute (array(
         $fruit -> name ,
         $fruit -> colour ,
         $fruit -> calories ,
    ));
}

 /* 提交更改 */
 $dbh -> commit ();

 /* 现在数据库连接返回到自动提交模式 */

```
```
/*  开始一个事务，关闭自动提交 */
 $dbh -> beginTransaction ();

 /* Change the database schema */
 $sth  =  $dbh -> exec ( "DROP TABLE fruit" );

 /* 更改数据库架构 */
 $dbh -> commit ();

 /* 现在数据库连接返回到自动提交模式 */

```
