#  quote() 语句转义处理
public string PDO::quote  ( string $string  [, int $parameter_type  = PDO::PARAM_STR  ] )
$string: 待转移语句
$paratemter_type : 转义风格?
;简单语句转义
$conn  = new  PDO ( 'sqlite:/home/lynn/music.sql3' );

$string  =  'Nice' ;
print  "Unquoted string:  $string \n" ;
print  "Quoted string: "  .  $conn -> quote ( $string ) .  "\n" ;
输出
```
Unquoted string: Nice
Quoted string: 'Nice'

```
```
;危险语句转义

$conn  = new  PDO ( 'sqlite:/home/lynn/music.sql3' );


$string  =  'Naughty \' string' ;
print  "Unquoted string:  $string \n" ;
print  "Quoted string:"  .  $conn -> quote ( $string ) .  "\n" ;

```
输出
```
Unquoted string: Naughty ' string
Quoted string: 'Naughty '' string'
;复杂语句转义
$conn  = new  PDO ( 'sqlite:/home/lynn/music.sql3' );


 $string  =  "Co'mpl''ex \"st'\"ring" ;
print  "Unquoted string:  $string \n" ;
print  "Quoted string: "  .  $conn -> quote ( $string ) .  "\n" ;

```
输出
```
Unquoted string: Co'mpl''ex "st'"ring
Quoted string: 'Co''mpl''''ex "st''"ring'

```
