# 进入mysql

    mysql --host=120.26.4.86 --port=3306 --user=root --password=tryme --database=xingbook_primary

# 导入sql文件

    mysql --host=120.26.4.86 --port=3306 --user=root --password=tryme --database=xingbook_primary < /root/vip.sql


# 导出指定数据库

    mysqldump --host=120.26.4.86 --port=3306 --user=root --password=tryme --databases disconf  > /root/disconf.sql
    
# 导出数据库指定表的结构和数据

    mysqldump --host=120.26.4.86 --port=3306 --user=root --password=tryme --databases xingbook_primary --tables vip_goods xbhb_vip_goods > /root/vip.sql
    
# 导出指定数据库所有的表结构

    mysqldump --host=120.26.4.86 --port=3306 --user=root --password=tryme --databases disconf --no-data > /root/disconf.sql
 