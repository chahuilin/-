# 用法：

    explain  select * from ems_expense_feedback  where expenseId=333
 
rows列 表示 sql执行时检索次数，越小越好

根据上面的结果再适当加上索引

## 1.加PRIMARY KEY（主键索引）：

    mysql>ALTER TABLE `table_name` ADD PRIMARY KEY ( `column` ) 

## 2.添加UNIQUE(唯一索引) 
    mysql>ALTER TABLE `table_name` ADD UNIQUE ( 
`column` 
) 

## 3.添加INDEX(普通索引) 

    mysql>ALTER TABLE `table_name` ADD INDEX index_name ( `column` ) 
## 4.添加FULLTEXT(全文索引)

    mysql>ALTER TABLE `table_name` ADD FULLTEXT ( `column`) 
## 5.添加多列索引 

    mysql>ALTER TABLE `table_name` ADD INDEX index_name ( `column1`, `column2`, `column3` )
