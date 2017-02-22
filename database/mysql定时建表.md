# 第一步，建函数

    CREATE  PROCEDURE `prc_z_ott_start_log`(in_num INT)
    BEGIN
    DECLARE  t_sql VARCHAR(4000);
    DECLARE  t_idx_1 VARCHAR(4000);
    DECLARE  t_idx_2 VARCHAR(4000);
    DECLARE  t_idx_3 VARCHAR(4000);
    DECLARE  t_date DATE;
    DECLARE  t_partion VARCHAR(300);
    DECLARE  table_part VARCHAR(50);
    DECLARE  num INT;
    SET num=0;
    SET t_date= DATE_ADD(NOW(), INTERVAL 0 DAY);
    WHILE num < in_num DO
    SELECT DATE_FORMAT (t_date,'%Y%m%d') INTO t_partion;
    SET table_part=CONCAT('z_ott_start_log_', t_partion);
    SELECT COUNT(1) FROM information_schema.tables WHERE table_schema='xingbook-log' AND table_name = table_part INTO @cnt;
    IF @cnt = 0 THEN
        SET t_sql= CONCAT('create table If Not Exists ',table_part,
    ' (   `id` int(11) NOT NULL AUTO_INCREMENT,   `total_read_time` bigint(20) DEFAULT NULL ,   `click_log` varchar(255) DEFAULT NULL ,   `read_count` int(11) DEFAULT NULL ,   `video_time` bigint(20) DEFAULT NULL ,   `video_count` int(11) DEFAULT NULL ,   `device` varchar(50) DEFAULT NULL ,   `os` varchar(50) DEFAULT NULL ,   `screen_resolution` varchar(50) ,   `ip` varchar(50) DEFAULT NULL ,   `create_time` datetime DEFAULT NULL ,   PRIMARY KEY (`id`) ) ENGINE=InnoDB DEFAULT CHARSET=utf8 ;');
    

    SET @sql=t_sql;
    PREPARE s1 FROM @sql;
    EXECUTE s1;
    DEALLOCATE PREPARE s1;

    END IF;
    SET num=num+1;
    SELECT DATE_ADD(NOW(), INTERVAL num DAY) INTO t_date;
    END WHILE;
    END

# 第二步，建事件

    CREATE  EVENT `prc_z_ott_start_log定时任务` ON SCHEDULE EVERY 5 DAY STARTS '2017-02-22 20:15:48' ON COMPLETION NOT PRESERVE ENABLE DO CALL prc_z_ott_start_log(7)