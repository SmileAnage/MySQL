MySQL数据库
===

[TOC]

### MySQL安装
1.安装服务端
>sudo apt-get install mysql-server

2.安装客户端
>sudo apt-get install mysql-client

3.启动服务端(启动 | 关闭 | 重启 | 状态)
>sudo /etc/init.d/mysql start | stop | restart | status

4.客户端连接
>msyql -u [user] -p [passwd]
>e.g : mysql -u root -p 123456

### 数据库操作
1.查看已有库
>show databases;

2.创建库(指定字符集)
>create database [database_user] [charset=utf8];

3.查看创建库的语句(字符集)
>show create database [database_user];

4.查看当前所在库
>select database();

5.选择数据库
>use [database_user];

6.删除数据库
>drop database [database_user]

### 数据表操作
* decimal(M,D)类型提高精度减少误差
>M:是数字的最大位数(精度)
>D:是小数点右侧数字的数目(标度),不能超过M 
>e.g:decimal(6,2) -9999.99 < 范围 < 9999.99
* char 和 varchar
>char:定长，效率高，一般用于固定长度的表单提交数据存储
>varchar:不定长，效率偏低
* text 和 blob
>text:用来存储非二进制文本
>blob:用来存储二进制字节串
* enum 和 set
>enum:用来存储给出的一个值
>set:用来存储给出的值中一个或多个值
>enum('男','女')  只能选一个
>set('男','女','不详')  可以多选
* 表的属性设置
> * 设置数字为无符号:**unsigned**
> * 设置字段不许为空:**NOT NULL**
> * 设置默认值:**DEFAULT** 后面跟默认值
> * 设置自增:**AUTO_INCREMENT** 一般用于ID
> * 设置主键，不许有重复:**PRIMARY KEY**

1.查看已有数据表
>show tables;

2.查看已有表的字符集
>show create table [table_user];

3.查看表结构
>desc [table_user];

4.删除表
>drop table [table_user];

### 数据基本操作
#### 插入(insert)
```python
insert into [table_user] values (value1), (value2),...;
insert into [table_user] (field1,field2,...) values (value1),...;
 * e.g. insert into smile values (1,'name1',23), (2,'name2',22);
```
#### 更新修改(update)
```python
update [table_user] set [field1] = [value1], [field2] = [value2] where id = 2;
 * e.g. update smile set name='小木', age=23 where id = 2; 
```
#### 删除表记录(delete)
```python
delete from [table_user] where [条件];
 * e.g. delete from smile where id = 2;
```
#### 表字段的操作(alter)
```python
 * 增加字段(add)
       alter table [table_user] add [field] [date_type];
       alter table [table_user] add [field] [data_type] first;
       alter table [table_user] add [field1] [data_type] after [field2];
 * 删除字段(drop)
       alter table [table_user] drop [field];
 * 修改数据类型(modify)
       alter table [table_user] modify [field] [new_data_type];
 * 修改字段名(change)
       alter table [table_user] change [old_field] [new_field] [new_data_type];
 * 表重命名(rename)
       alter tbale [table_user] rename [new_table_user];
```
#### 表的查询(select)
```python
select * from [table_user] [where 条件];
select [field1],[field2] from [table_user] [where 条件];
```
#### where子句
 * where子句在sql语句中扮演这重要的角色，主要通过一定的运算条件进行数据的筛选
 * MySQL主要有一下几种运算符
>算术运算符
>比较运算符
>逻辑运算符
>位运算符

1.清空表数据
>truncate table [table_user];

2.升序(默认为升序)
>select * from [table_user] order by [field] [asc];

3.降序
>select * from [table_user] order by [field] desc;

4.分页显示( limit [nums] )
>select * from [table_user] order by [field] limit [nums];

5.多表查询
>select * from [table_user1] join [table_user2] on [field1] = [field2];
> * e.g. select * from user join sex on sex=Sid;
> user表中的sex用1和2表示,sex表中１,代表男，２代表女，让相等的两个字段连接．

6.在两者之间( between )
>select * from [table_user] where [field] between [条件1] and [条件2];

7.在集合中( in )
>select * from [table_user] where [field] in (条件1, 条件2);

8.模糊查找( like (%)代表不等值, (_)代表一个值)
>select * from [table_user] where [field] like ('%小木%');
>查找名字字段中包含　小木　的数值

9.为空( is null )
>select * from [table_user] where [field] is null; 

10.逻辑关系( or and not )
>select * from [table_user] where [field1] = [条件1] or [field2] = [条件2]; 
>select * from [table_user] where [field1] = [条件1] and [field2] = [条件2];
>select * from [table_user] where not [field] = [条件];

### 数据库备份与还原
1.数据库备份
>mysqldump -u root -p [备份的数据库名] > 存储位置/*.sql

2.数据库恢复
>mysql -u root -p [需要恢复到的数据库名] > 存储位置/*.sql











