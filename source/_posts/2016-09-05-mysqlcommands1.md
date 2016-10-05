---
title: MySQL常用命令(1)
date: 2016-09-05 23:33:22
tags:
 - MySQL
 - Database
categories: 编程
---

> 好消息是半泽直树第二季还有3个月就来了

数据科学没有扎实的数据库知识是玩玩不行的。在sql数据库中，MySQL学好了上手其它的数据库语言非常方便。在这里记几个常用的MySQL语言方便查询。<!---more--->

 - 将数据库或表从数据库中导出sql文件
    - 在cmd 输入 mysqldump -u username -p -h host 'database' 'table' > yourfile.sql
 - 将sql文件导入数据库
    - 先登录mysql，在shell输入source /path/to/your/file, 或者使用mysqldump， 只需要将'>'改成'<'就可以了
 - 将数据库中的表导出
    - 先登录mysql，在shell输入 ‘SELECT * FROM dbname INTO OUTFILE '/tmp/data.txt' FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"' LINES TERMINATED BY '\n';’ 可以正常使用sql语言，并且支持txt和csv的输出
 - 对已有的表进行修改
    - 在mysql里，使用语句‘ALTER tbname DROP/ADD colname  TYPE CHARACTER SET’来添加和删除列或关键值(Primary Key)， 添加时注意设置格式和编码格式。使用语句‘ALTER tbname CHANGE colname colname1 TYPE CHARACTER SET’ 来改名和修改格式及编码格式。
 - 一般的建表语句
    - 在mysql里，使用 ‘CREATE tbname (col1 TYPE CHARACTER SET utf8mb4 NOT NULL col2 TYPE CHARACTER SET utf8mb4 AUTO_INCREMENT, PRIMARY KEY (col1, col2));’
 - 一般的插入语句
    - 在mysql里， 使用‘INSERT tbname (col1, col2) VALUES (value1, value2) ON DUPLICATE KEY UPDATE;’

关于MySQL中选择的语句介绍之后会写，特别是关于group by和join的用法。
