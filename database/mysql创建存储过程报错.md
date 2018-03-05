mysql创建存储过程或者函数：

    mysql> create procedure pr_gen_users()  
        -> begin  
        ->  select * from tb_user;  
    ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that  
    corresponds to your MySQL server version for the right syntax to use near '' at  
    line 3  
    mysql> end;  
    ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that  
    corresponds to your MySQL server version for the right syntax to use near 'end'  
    at line 1  
    mysql> 
    
默认情况下，创建存储过程会报错，这是因为默认的分隔符是;，而里面已经有了一个分隔符。换一下分隔符就不会报错了

    mysql> delimiter //  
    mysql> create procedure pr_gen_users()  
        -> begin  
        ->  select * from tb_user;  
        -> end //  
    Query OK, 0 rows affected (0.00 sec)