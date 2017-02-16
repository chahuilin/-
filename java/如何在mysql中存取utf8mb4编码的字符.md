utf8编码可以支持一到4字节的字符编码，在MySQL用我们一般使用utf8编码来处理字符类型，通常情况下都没有问题，但遇到4字节编码的字符，在数据存取的时候就会有问题了。
通常我们可能会得到一个错误或者警告：Incorrect string value: '\xF0\x9D\x8C\x86' for column ...
Mysql 从5.5.3版本开始支持4字节的utf8编码，如果你的Mysql数据库是5.5.3+，按照以下步骤就能解决这个问题，如果版本低于5.5.3，是不是可以考虑升级数据库版本呢？
1、在修改数据库编码前先对数据库备份（虽然utf8mb4兼容utf8，但有备无患）
2、修改数据库的编码、表的编码、列的编码为utf8mb4
3、在Mysql数据库配置文件(my.ini)中加入如下设置

    [client]  
    default-character-set = utf8mb4  
    
    [mysql]  
    default-character-set = utf8mb4  
    
    [mysqld]  
    character-set-client-handshake = FALSE  
    character-set-server = utf8mb4 //这行最主要  
    collation-server = utf8mb4_unicode_ci  

重新启动Mysql数据库，确认设置生效

    mysql> show VARIABLES like '%char%';  
    +--------------------------+----------------------------------------+  
    | Variable_name            | Value                                  |  
    +--------------------------+----------------------------------------+  
    | character_set_client     | utf8                                   |  
    | character_set_connection | utf8                                   |  
    | character_set_database   | utf8mb4                                |  
    | character_set_filesystem | binary                                 |  
    | character_set_results    | utf8                                   |  
    | character_set_server     | utf8mb4                                |  
    | character_set_system     | utf8                                   |  
    | character_sets_dir       | /home/app/mysql-5.5.33/share/charsets/ |  
    +--------------------------+----------------------------------------+  
    8 rows in set  

4、在获取数据库连接的时候执行sql：set names utf8mb4;我使用的是alibaba的开源数据库连接池程序，在配置文件中增加一行如下配置

    <property name="connectionInitSqls" value="set names utf8mb4;" />  