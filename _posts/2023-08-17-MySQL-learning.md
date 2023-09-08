---
layout: post
title: "MySQL学习"
data:  2023-08-17
categories: Tutorials
tags:  Tutorial Coding Learning Database MySQL
---

* content
{:toc}

## 基本用法
### 登录

`mysql -u <user name> -p -h <host name>`
如过没设置密码就跳过`-p`，如过本地登录就省掉`<host name>`。
root用户默认是没有密码的，通过该命令可设置密码：`mysqladmin -u root password "your_new_password"`
root用户登录后可创建新用户：`CREATE USER 'username'@'localhost' IDENTIFIED BY 'your_password';`

### 创建数据库

MySQL的语法其实就是平铺直叙的文本，通常用大写表示命令。每个独立命令须用`;`表示结尾，可以随意换行，跟C语言一样。
显示已有数据库：`SHOW DATABASES;`
使用某数据库：`USE <database name>`
创建数据库：`CREATE DATABASE <database name>(
    // <col name> <data type> <constrain>
    id varchar(60) primary key,
    seq text
)`
删库：`DROP DATABASE <database name>`


### 操作表

```shell
#查看表中前几行：
SELECT * FROM <table name> LIMIT <row count>
#查看表信息：
DESCRIBE <table name>
#查询：
SELECT * FROM <table name> WHERE <condition>
#删除表：
DROP TABLE <table name>
#删除数据：
DELETE FROM TABLE WHERE <condition>
#清空
TRUNCATE <table name>
#或者
DELETE FROM <table name> # 前者快速删除不可回滚，后者逐条删除，可回滚。

# 查看表信息
SHOW TABLE STATUS LIKE <table name> \G

```

### 约束

用于限制表中的数据，为了保证表中数据的准确性和可靠性,不符合约束的数据，插入时就会失败。

|名称|作用|
|-----|-----------------|
|NOT NULL|	非空，用于保证该字段的值不能为空|
|DEFAULT|	默认值，用于保证该字段有默认值|
|PRIMARY KEY|	主键，用于保证该字段的值具有唯一性并且非空|
|UNIQUE|	唯一，用于保证该字段的值具有唯一性，可以为空|
|CHECK|	检查约束（MySql不支持），检查字段的值是否为指定的值|
|FOREIGN KEY|	外键，用于限制两个表的关系，用于保证该字段的值必须来自于主表的关联列的值，在从表添加外键约束，用于引用主表中某些的值|


### 导入数据

```shell
# 逐行导入数据
INSERT INTO <table name> (<col1>, <col2>, <col3> ... ) VALUES (<value1>, <value2>, <value3> ...)

# 更新数据
UPDATE <table name> SET `<col name>` = <value> `<col name>` = <value> where <condition> #如过不设置codition就对整张表进行更新
# 删除数据
DELETE FROM TABLE WHERE <condition>
# 批量导入，确保local-infile 设置为on
set global local_infile=on
# 或者在登录的时候加上 --local_infile=1
# 查询local-infile 状态
SHOW GLOBAL VARIABLES LIKE "local_infile"
# 然后就可以导入了
LOAD DATA INFILE <file path> 
INTO <table name> 
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
ENCLOSED BY '"'
CHARACTER SET utf8
IGNORE <num> ROWS


# 使用source file.sql批量导入
# 设置关键参数
set sql_log_bin=OFF;//关闭日志
set autocommit=0;//关闭autocommit自动提交模式
START TRANSACTION;//开启事务
source <path to .sql file>
```


## 参考信息源

1. [MySQL新手快速入门](https://blog.csdn.net/m0_58878709/article/details/128817956)
2. [mysql快速导入多个大csv文件](https://blog.csdn.net/weixin_37095828/article/details/104167399)
