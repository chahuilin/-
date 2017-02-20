mysql版本为：5.6.19，Mysql5.6版本对安全性进行了增强
在使用mysql的导出命令进行数据库备份时，出现：

    Warning: Using a password on the command line interface can be insecure;

是因为在导出命令中使用了-ppassword所导致的，解决方法是：
1、使用my.cnf来存储密码，格式如下：

    [mysqldump]
    user=root
    
    password=root

2、在mysqldump命令行使用 --defaults-file属性来指定my.cnf的位置

    mysqldump -u用户名 -p 密码  数据库名 表名> 导出的文件名(mysqldump -uroot -pjiaozhujun  xingbook suber> suber.sql) 

    mysqldump --defaults-file="my.cn" -uroot  xingbook suber> suber.sql

详细的：

    mysqldump --defaults-file=".mylogin.cnf" -hlocalhost -P3306 --user=root --routines --default-character-set=utf8 --max_allowed_packet=1G testdb> testdb.sql