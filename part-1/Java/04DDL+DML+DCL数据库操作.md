# 1 数据类型

## 1.0 扩展知识

- 进制
  - 进制:
  - 二进制(0,1)
  - 十进制(0-9)
  - 8进制(0-7)
  - 16进制(0-F)
- 数据类型
  - 计算机内存存储数据,针对不同的数据,划分不同的数据类型
- ascii
  - 有字母,有标点,有符号
- utf8  
  - 有中文,有字母,有标点,有符号

## 1.1 数据类型分类

- 整型数据类型(0,1,2,3...)

  int

  ![image-20220113114542128](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220113114542.png)

- 小数数据类型--浮点数(1.2)

  float  

  ![image-20220113114624042](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220113114624.png)

- 字符串数据类型

- varchar---可变字符型  

  char ---定长字符型   

  ![image-20220113114719005](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220113114719.png)

- 二进制类型

  ![image-20220113114945587](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220113114945.png)

- 时间日期类型

  ![image-20220113115013113](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220113115013.png)





# 2 数据库操作

>SQL = DQL+DDL+DML+DCL
>

## 2.1 DDL数据定义语言

- 术语
  - 关键字：对当前程序拥有特定含义的单词
  - DDL的关键字:create,alter,drop
- 作用：
  - 创建---create
    - 创建数据库
    - 创建表
  - 修改---alter
    - 修改数据库字符集
    - 修改表名,修改表列,修改数据类型
  - 删除---drop
    - 删除数据库
    - 删除表
- 手段
  - 通过navicat界面操作数据库
    - 创建
      - 选中连接名--鼠标右键--选择创建数据库-输入数据库名-字符集选择倒数第二个-排序规则选择第一个
      - 数据库名规则:1不能是中文 2不能是关键字 3 不能重名 4不能以数字开头5不能有特殊符号,但不限于_ @$
    - 修改
      - 选中数据库--鼠标右键--数据库属性--修改数据库字符集
    - 删除
      - 选中数据库---鼠标右键---选择删除数据库
  - 通过navicat界面操作表
    - 创建
      - 双击数据库---选中表-鼠标右键---选中新建表---输入列名,选择数据类型,输入长度---添加栏位---输入列名,选择数据类型,输入长度---点击保存---输入表名---点确定
    - 修改
      - 选中表---鼠标右键---点击重命名---输入新的表名
      - 选择表---鼠标右键---设计表---添加栏位---输入新列名,选择数据类型---点保存
      - 选中表---鼠标右键---设计表---修改列名---选择新的数据类型---点击保存
    - 删除
      - 选中表---鼠标右键---选中列,点击删除栏位---点击保存
      - 选中表---鼠标右键---点击删除表
  - 通过命令

```mysql
# SQL=DQL+DDL+DML+DCL
# DQL=数据查询语言--查询
# DDL=数据定义语言--对数据库和表结构进行创建,修改,删除
# DML=数据操作语言--对表内容进行新增,修改,删除
# DCL=数据控制语言--对用户权限进行增加,修改,删除

# 前提知识:
# 进制:二进制(0,1),十进制(0-9),8进制(0-7),16进制(0-F)


# *******DDL ************
# ****01 创建数据库
# 语法：create database 数据库的名字 charcater set utf8;
# 作用：创建一个数据库
# 数据的名字有规则的不能随便瞎写
# 1不能是中文 2不能是关键字 3 不能重名 4不能以数字开头5不能有特殊符号,但不限于_ @$
# 案例:创建一个数据库,数据库名字为class
create database class character set utf8;
# 查看数据库
show databases;
# *****02 修改数据库字符集****
# 语法:alter database 数据库名字 character set 字符集;
# 案例:修改class数据库的字符集为ascii
alter database class character set utf8;
# ****03 删除数据库*****
# 语法:drop database 数据库名;
# 案例:删除数据库class
drop database class;
# 查看数据库
show databases;

# 练习:创建一个数据库,数据库名字为woniusales
create database woniusales character set utf8;
# 练习:修改woniusales数据库的字符集为ascii
alter database woniusales character set ascii;
# 练习:删除数据库woniusales
drop database woniusales;

# ******01 创建表 *********
# 语法：create table 表名 (列名1 数据类型1,列名2 数据类型2,.....);
# 作用：创建一个表，表里包含多少列
# 案例:创建一个数据库db_class,在这个数据库下,创建一个表,
# 表名为tb_class222,列为cid 数据类型为int,cname 数据类型为varchar,长度为5
# 创建一个数据库
create database db_class;
# 查看数据库
show databases;
# 选择数据库
use db_class;
# 创建一个表
create table  class222(
	cid int,
	cname varchar(5)
);
# 查看表
select * from class222;
show tables;

# 练习:创建一个数据库db_woniusales,在这个数据库下,
# 创建一个表为tb_stu,列为sid 数据类型为int,sname 数据类型为varchar ,长度为5
# 创建数据库
create database db_woniusales character set utf8;
# 选择数据库
use db_woniusales;
# 新建表
drop table if exists tb_stu;
create table tb_stu (
sid int,
sname varchar(5)
);
# 查看表
show tables;
select * from tb_stu;
# 查看表结构
desc tb_stu;


# ******02 修改表名字
# 语法：alter table old_tbname rename new_tbname;
# 作用：修改表的名字为新表名
# 案例:给表class222改个新名字为class
# 选择数据库
use db_class;
# 修改表名
alter table class222 rename class;
# 查看表名
show tables;
# 练习:给表tb_stu改个新名字为tb_student
use db_woniusales;
alter table tb_stu rename tb_student;
show tables;


# ******03 给表添加列
# 语法1：alter table 表名 add 列名1 数据类型;
# 作用：给表添加列
# 案例:给表class添加一个列loc1,数据类型为int
use db_class;
alter table class add loc1 int;
desc class;

# 练习:给表tb_student添加列age,数据类型为varchar 长度为1,列ssex,数据类型为varchar 长度为1
# 选择数据库
use db_woniusales;
# 查看表结构
desc tb_student;
# 增加多列
alter table tb_student add age varchar(1),add ssex varchar(1);
alter table tb_student add (age varchar(1),ssex varchar(1));
# 查看表结构
desc tb_student;
# 思考如何一条命令加入多列?

# ******04 修改列的名字以及数据类型
# 语法：alter table tbname change 旧列名 新列名 新的数据类型;
# 作用：修改列的名字同时也可以修改数据类型
# 案例: 修改loc1名字为新名字loc,新的数据类型为varchar,长度为10
use db_class;
desc class;
alter table class change loc1 loc varchar(5),change cid1 cid int;
desc class;


# 练习:修改tb_student表的age名字为新名字sage,新的数据类型为int
alter table tb_student change age sage int;

# ******05 删除列
# 语法：alter table 表名 drop 列名1;
# 作用：删除表的某个列
# 案例:删除class表的loc列
desc class;
alter table class drop loc;
desc class;
# 练习:删除tb_student表的ssex列
alter table tb_student drop ssex;
# ******06 删除表
# 语法：drop table 表名;
# 作用：删除某张表
# 案例: 删除tb_class表
# 删除表
drop table class;
# 查看表
show tables;
# 练习: 删除tb_student表
drop table tb_student;
```

## 2.2 DML数据操纵语言

- 术语
  - 关键字 insert into , update,delete
- 作用
  - 增加数据
    - insert into
  - 修改数据
    - update
  - 删除数据
    - delete
- 手段
  - navicat
    - 增加数据:双击表名,点击左下角+号,输入数据,点击左下角√
    - 修改数据:双击表名,双击数据栏,输入数据,点击左下角√
    - 删除数据:双击表名,点击左下角-号,输入数据,点击左下角√
  - 命令

```mysql
# ******01 新增数据********
# 语法：insert into 表名[(列1, 列2,... 列n)] values(列1的值, 列2的值,...列n的值),(列1的值, 列2的值,...列n的值)..;
# 作用：给表添加一行新的数据
# 案例:新增一个student表,sid int,sname varchar(10),ssex varchar(2),sage int,
create table student(
sid int,
sname varchar(10),
ssex varchar(2),
sage int);
# 显示所有的表
show tables;
# 查看表内容
select * from student;
# 新增数据方法一
insert into student values (1,'张三','男',18);
# 新增数据方法二
insert into student(sname,sid,sage,ssex) values ('张三',2,18,'男');
# 新增数据方法三
insert into student(sname,sid,ssex) values ('张三',4,'男'),('张三',5,'男'),('张三',6,'男');
# 查看表内容
select * from student;

# 练习:新增一个student表,sid int,sname varchar(10),ssex varchar(2),sage int,以三种形式分别插入一条合适数据.
create database stu character set utf8;

show databases;
use stu;
create table student(
sid int,
sname varchar(10),
ssex varchar(2),
sage int);
insert into student(sname,sid,ssex) values ('张三',3,'男');
# 思考:如何使用一条命令新增多条数据?


# *******02 修改数据************
# 语法：update 表名 set 列 = 值 where 条件;
# 作用：更新表中的列的值
# 案例1:修改student表的年龄为20岁
select * from student;
update student set sage = 20;

# 案例2:修改student表的学生id为1的年龄为200岁
update student set ssex ='男女男女' where sid = 1;

# 练习:修改姓名为xxx的性别为男


# 案例:修改年龄最大的人岁数为10岁
update student set sage = 10 where sage = (select * from (select max(sage) max_sage from student) b);  # 套select  把student的数值给了另一个表b
select * from student;

# ****03 删除数据******
# 语法：delete from 表名 where 条件;
# 作用：删除表中的数据
# 案例:删除student表中编号为2的信息
# 加where条件的删除
delete from student where sid =2;
# 查看所有数据
select * from student;
# 不加where条件的删除
delete from student;
# 查看所有数据
select * from student;
# 思考问题:drop和delete都是删除,有什么区别?
# 1.drop删除表,delete是删除
# 2.drop的运行速度比delete
```

## 2.3 DCL数据控制语言

- 术语
  - grant  授权
  - revoke  解除授权
  - 所有权限：all privileges
  - 其他权限:select 查询权限 update 修改权限 insert 插入数据权限 delete 删除数据权限



- 语法
  - 授权
  - grant 权限 on 数据库.表 to 用户@主机ip;
  - 解除授权
  - revoke 权限 on 数据库.表 from 用户@主机ip;
  - 刷新权限
  - flush privileges
  - %代表所有主机
- 举例

```mysql

# *****DCL*****
# 对数据库用户进行授权
# 权限:select 查 update 修改 delete 删除 
# 所有权限:all privileges
# 语法:grant 权限 on 数据库.表 to 用户@主机ip;
# 解除授权
# 语法:revoke 权限 on 数据库.表 from 用户@主机ip;
# 刷新权限:flush privileges
# %代表所有的ip地址
# 新建用户：
create user 用户名 identified by '密码';
# 删除用户:
drop user 用户名;

# 1.新建一个aaa用户
create user aaa identified by '123456';
# 2.使用aaa用户登录连接

# 3.使用root用户给予aaa所有权限
grant all privileges on *.* to aaa@'%';
# 4.关闭连接,在重新打开连接即可看到所有的数据库和表

# 5.使用root用户收回aaa用户的权限
revoke all PRIVILEGES on *.* from aaa@'%';
# 6.刷新权限
flush privileges
# 7.删除aaa用户
drop user aaa;
```

