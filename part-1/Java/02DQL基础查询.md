# 1 DQL基础查询

>SQL = 结构化查询语句
>
>DQL=数据查询语言
>DDL=数据定义语言
>DML=数据操作语言
>DCL=数据控制语言



## 1.1 单表简单查询

- 准备工作
  - 构造数据 = emp+dept

```mysql
# DDL的命令
create table dept(
	deptno int primary key auto_increment, -- 部门编号
	dname varchar(14) ,	  -- 部门名称
	loc varchar(13)   -- 部门地址
) ;

# DML的命令
insert into dept values(10,'财务部','北京');
insert into dept values(20,'研发部','上海');
insert into dept values(30,'销售部','广州');
insert into dept values(40,'行政部','深圳');

# DDL的命令
create table emp(
	empno int primary key auto_increment, -- 员工编号
	ename varchar(10), 					-- 员工姓名					
	job varchar(9),	-- 工作岗位
	mgr int,	 -- 上级领导
	hiredate date, -- 入职日期
	sal int, -- 工资
	comm int,  -- 奖金
	deptno int not null, -- 部门编号
	foreign key (deptno) references dept(deptno)
);

# DML的命令
insert into emp values(7369,'刘一','职员',7902,'1980-12-17',800,null,20);
insert into emp values(7499,'陈二','推销员',7698,'1981-02-20',1600,300,30);
insert into emp values(7521,'张三','推销员',7698,'1981-02-22',1250,500,30);
insert into emp values(7566,'李四','经理',7839,'1981-04-02',2975,null,20);
insert into emp values(7654,'王五','推销员',7698,'1981-09-28',1250,1400,30);
insert into emp values(7698,'赵六','经理',7839,'1981-05-01',2850,null,30);
insert into emp values(7782,'孙七','经理',7839,'1981-06-09',2450,null,10);
insert into emp values(7788,'周八','分析师',7566,'1987-06-13',3000,null,20);
insert into emp values(7839,'吴九','总裁',null,'1981-11-17',5000,null,10);
insert into emp values(7844,'郑十','推销员',7698,'1981-09-08',1500,0,30);
insert into emp values(7876,'郭十一','职员',7788,'1987-06-13',1100,null,20);
insert into emp values(7900,'钱多多','职员',7698,'1981-12-03',950,null,30);
insert into emp values(7902,'大锦鲤','分析师',7566,'1981-12-03',3000,null,20);
insert into emp values(7934,'木有钱','职员',7782,'1983-01-23',1300,null,10);
```

- 01 全查询

```mysql
#  *************01 全查询***********
# 语法:select 结果 from 表名;
# 作用:查询表里的所有数据
# 案例:查询emp表里的所有信息
# 结果:*     *代表所有
# 表:emp
select * from emp;
# 练习:查询dept表里的所有信息
# 结果:*     *代表所有
# 表:dept
select * from dept;
```

- 02 部分列查询

```mysql
# **********02 部分列查询************
# 语法：select 列名1,列名2,... from 表名;
# 作用：查询某些列的数据
# 案例: 查询员工的姓名和工资以及提层
# 分析
# 表名: emp
# 列名:ename,sal,comm
select ename,sal,comm from emp;
# 案例: 查询部门名称和部门地址
# 分析
# 表:dept
# 列名:dname,loc 
select dname,loc from dept;
# 练习: 查询员工姓名和员工编号
# 分析
# 表:emp
# 列:ename,empno
select ename,empno from emp;
```

- 03 列别名

```mysql
# **********03 起别名*****************
# 语法：select 列名1 别名1,列名2 别名2,... from 表名;
# 作用：对列起别名
# 案例:查询员工的姓名和工资,并且给列起中文名字
# 分析
# 表:emp
# 结果:ename '员工姓名',sal '员工工资'
select ename '员工姓名',sal '员工工资' from emp;
# 练习:查询员工姓名和工作岗位,并且对列起中文名字
# 分析
# 结果:ename'员工姓名',job '工作岗位'
# 表:emp
select ename'员工姓名',job '工作岗位' from emp;

# 补充知识点:对表起别名
# 语法:select 列名1 别名1,列名2 别名2,... from 表名 表别名; 学多表查询的时候使用
# 练习:查询员工姓名和工作岗位,并且对表起别名
select e.ename '员工姓名',e.job '工作岗位' from emp e;
```

- 04 部分行查询

```mysql
# ********04 部分行(限制行,分页)查询****************
# 语法：select 结果 from 表 limit m,n;(m代表起始行-1,n代表查询多少行数据)
# 作用：查询某些行数据
# 案例:查询员工表信息的前五行数据(1-5)
# 分析
# 结果:*
# 表:emp
# 限制行:limit 0,5
select * from emp limit 0,5;

# 案例:查询部门表第2条至第4条数据
# 分析
# 结果:*
# 表:dept
# 限制行:limit 1,3
select * from dept limit 1,3;

# 练习:查询员工表信息的第三行数据到第七行数据(3-7)
# 分析
# 结果:*
# 表:emp
# 限制行:2,5
select * from emp limit 2,5;
# 练习:查询第2到第8的员工工资和员工姓名(2-8)
# 分析
# 结果:sal,ename
# 表:emp
# 限制行:limit 1,7
select sal,ename from emp limit 1,7;
# 练习:查询员工姓名和工资,起别名为"姓名"和"工资",并且只显示第2-3行
# 分析:
# 结果:ename "姓名",sal "工资"
# 表:emp
# 限制行:limit 1,2
select ename "姓名",sal "工资" from emp limit 1,2;

```

- 05 排序

```mysql
# *********05 排序查询***********
# 语法1：select 结果 from 表 order by 排序列 asc/desc(asc正序,desc倒序);(对单列进行了排序)
# 作用：对表数据进行按一定的方式排序
# 案例1:查询员工工资,工资按照倒序排序
# 分析:
# 结果:sal
# 表:emp
# 排序:order by sal desc 
select sal from emp order by sal desc;

# 语法2: select 结果 from 表 order by 排序列1 asc/desc,排序列2 asc/desc(asc正序,desc倒序);
# 案例2:查询员工工资和入职时间,工资按照倒序排列,当工资一样的时候,按照入职时间正序排列(只有当第一列数据有相同项的时候,才有对第二列排序的意义)
# 分析
# 结果:sal,hiredate
# 表:emp
# 排序:order by sal desc,hiredate asc
select sal,hiredate from emp order by sal desc,hiredate asc;

# 练习1:查询员工姓名和工资,工资按照倒序排序,且列名显示姓名和工资
# 分析
# 结果:ename '姓名',sal '工资'
# 表:emp
# 排序:order by sal desc
select ename '姓名',sal '工资' from emp order by sal desc;
# 练习2:查询部门表信息,部门编号按照正序排序
# 分析
# 结果:*
# 表:dept
# 排序:order by deptno
select * from emp order by deptno;
# 练习3:查询员工工资和奖金,工资按照正序排列,当工资一样的时候,按照奖金倒序排列
# 分析
# 结果:sal,comm 
# 表:emp
# 排序:order by sal , comm desc
select sal,comm from emp order by sal , comm desc;
# 练习4:查询工资最高的前三位员工信息
# 分析
# 结果:*
# 表:emp
# 排序:order by sal desc 
# 限制行:limit 0,3
select * from emp order by sal desc limit 0,3;
```

- 06 运算符

```mysql
# ***** 06 运算符********
# 1.比较运算符
# > = < >= <= !=
# 2.逻辑运算符
# 与或非 and or not 
# 甲 and 乙  甲为真并且乙为真   为真
# 甲 or 乙   甲为真或者乙为真   为真  
# 3.算数运算符
# + - * /
```

- 07 条件查询

```mysql
# ******07 条件查询******
# *****07.01精确查询
# 语法：select 结果 from 表名 where 条件;
# 作用：从表中查询符合条件的数据
# *****07.01.01单条件查询************
# 案例1：查询emp表中工资等于3000的员工信息
# 结果:*
# 条件:sal = 3000
# 表:emp
select * from emp where sal = 3000;

# 案例2: 查询工资大于2000的员工信息
# 结果:*
# 条件:sal > 2000
# 表:emp
select * from emp where sal > 2000;

# 练习1 查询姓名为张三的员工信息
# 结果:*
# 条件:ename = '张三'
# 表:emp
select * from emp where ename = '张三';

# 练习2 查询工资高于1000的员工信息
# 结果:*
# 条件:sal > 1000
# 表:emp
select * from emp where sal > 1000;


# *****07.01.02多条件查询**************
# 案例：计算工资大于1000并且小于3000的员工信息
# 结果:*
# 条件:sal > 1000 and sal < 3000
# 表:emp
select * from emp where sal > 1000 and sal < 3000;

# 案例：计算工资大于3000或者小于1000的员工信息
# 结果:*
# 条件:sal > 3000 or sal < 1000
# 表:emp
select * from emp where sal > 3000 or sal < 1000;

# 案例：计算工资大于等于1000并且小于等于3000的员工信息
# 结果:*
# 条件:sal >= 1000 and sal <= 3000
# 表:emp
select * from emp where sal >= 1000 and sal <= 3000;
# between and     [1000,3000]
select * from emp where sal between 1000 and 3000;
select * from emp where 1000 <= sal <= 3000;  -- 不允许这么写  mysql宽松 不报错但是显示错误数据
# 案例: 查询所有员工的工资增加200元的员工信息
# 结果 *,sal+200
# 条件:
# 表:emp
select  emp.*,sal+200 '增加后的工资' from emp;

# 练习1:查询工资高于1000,并且工资小于4000的员工信息
# 结果:*
# 条件:sal > 1000 and sal < 4000
# 表:emp
select * from emp where sal > 1000 and sal < 4000;
# 练习2:查询部门编号为10或者工作岗位为推销员的员工信息
# 结果:*
# 条件:deptno = 10 or job = '推销员'
# 表:emp
select * from emp where deptno = 10 or job = '推销员';
# 练习3:查询所有员工的工资增加20%的员工姓名和增加后的工资
# 结果:ename,sal*1.2
# 表:emp
select ename,sal*1.2 '增加后的工资' from emp;


# 07.02模糊查询
# 语法：select 结果 from 表 where 列 like "通配符+条件"
# 通配符：_ 占位1位 % 占位0-N

# 作用：查找某列像什么的数据
# 案例:查询名字是两个字符的员工信息
# 结果:*
# 条件:ename like '__'
# 表:emp
select * from emp where ename like '__';

# 案例:查询姓李的员工信息
# 结果:*
# 条件:ename like '李%'
# 表:emp
select * from emp where ename like '李%';

# 练习:查询姓名中包含十的员工信息
# 结果:*
# 条件:ename like '%十%'
select * from emp where ename like '%十%';
# 练习:查询姓名中第三个字符为一的员工信息
# 条件:ename like '__三%'
select * from emp where ename like '__三%';
# 练习:查询姓王的员工信息
# 结果:*
# 条件:ename like '王%'
# 表:emp
select * from emp where ename like '王%';
```

- 练习题

```mysql
1.查询部门为20的员工信息
2.查询部门为20的工资最高的员工信息
3.查询姓名长度为2的员工信息
4.查询部门10且工资大于3000的员工信息
5.查询员工姓名、工作、工资
6.查询员工姓名以及薪金，并按照薪金倒序排序
	(此处使用ifnull(列，设置值),作用如果列的值为null，则强制设置为设置值，ifNull(comm,0))
```





## 1.2 单表复杂查询

- 01 去重查询

```mysql
# *************DQL复杂查询*************
# *************01 去重查询**************
# 语法：select distinct 去重列 from 表;
# 作用：查询表中某列不重复的值
# 案例：查询公司的工作岗位有哪些 
# 结果:job
# 表:emp
# 条件:distinct job
select distinct job from emp;
```

- 02 集合操作

```mysql
# ************02 集合操作**************
# 语法：select 结果 from 表 where 列名 in(x,y,z,....);   (1,2,43,6,7)集合
# 作用：查询表中列的值在什么集合中的信息
# 案例：查询部门编号为10,20,30,40的员工信息
# 结果:*
# 表:emp
# 条件:deptno in (10,20,30,40)
select * from emp where deptno in (10,20);
select * from emp where deptno = 10 or deptno = 20;

# 练习1:查询部门编号不为20,30,40的员工信息(使用两种方法写)
# 练习2:查询工资大于等于1000小于等于3000的员工信息(使用两种方法写)



```

- 03 内置函数-聚合函数

```mysql
# ************03 聚合函数********************
# 作用函数:可以实现一定功能的字符()
# max(列名):求表中该列的所有值中的最大值
# min(列名):求表中该列的所有值中的最小值
# sum(列名):求表中该列的所有值的和
# avg(列名):求表中该列的所有值的平均值
# count(列名)：求表中该列的所有的值的个数
# 语法:select 聚合函数 from 表;
# 案例：求公司发放的工资总和
# 结果:sum(sal)
# 表: emp
select sum(sal) '工资总和'  from emp;-- 垃圾数据

# 案例：求员工的平均工资
# 结果:avg(sal)
# 表: emp
select avg(sal) from emp;

# 案例：求部门为20的员工的平均工资
# 结果:avg(sal)
# 条件:deptno = 20
# 表:emp
select avg(sal) from emp where deptno = 20;

# 练习1:求公司的最低工资
# 练习2:求公司的平均工资
# 练习3:求部门20最高工资
# 练习4:求部门20最低工资
# 练习5:求公司员工总数
# 练习6:求公司有奖金的员工人数( where comm is not null)
```







- 04  分组查询

```mysql
    # ***********04 分组查询****************
    # 语法：select 结果(要么是聚合函数,要么是分组列) from 表 where 条件 group by 分组列 having 条件(要么是聚合函数,要么是分组列);
    # 作用：对表中的列进行分组,只要出现"各",就一定用分组
    # 案例:查询各部门的人数以及部门编号
    # 结果:count(*),deptno
    # 条件:group by deptno
    # 表:emp
    select * from emp group by deptno;
    select count(*),deptno from emp group by deptno;

    # 案例:查询工资大于1500的各个部门人数以及部门编号
    # 结果:count(*),deptno
    # 条件:where sal > 1500
    # 表:emp
    # 分组:group by deptno
    select deptno,count(*) from emp where sal > 1500 group by deptno;


    # 案例:查询各个部门人数大于3人的部门编号和部门人数
    # 结果:deptno,count(*)
    # 条件:having count(*)>3
    # 分组:group by deptno
    # 表:emp
    select deptno,count(*) from emp group by deptno having count(*)>3;


    # 练习:查询工资高于1000的各部门人数
    # 结果:count(*)
    # 条件:where sal >1000
    # 分组:group by deptno
    # 表:emp
    select count(*),deptno from emp where sal > 1000 group by deptno;

    # 练习:查询部门的员工人数大于5的各个部门和人数
    # 结果:count(*),deptno
    # 条件:count(*) > 5
    # 分组:group by deptno
    # 表:emp
    select count(*),deptno from emp group by deptno having count(*) > 5;

    # 练习:查询工作为两个字符的各部门的人数
    # 结果:count(*),deptno
    # 条件:where job like '__'
    # 分组:group by deptno
    # 表:emp
    select count(*),deptno from emp where job like '__' group by deptno;

    # 练习:查询工资高于1000且小于4000的各部门人数
    # 结果:count(*),deptno
    # 条件:where sal > 1000 and sal < 4000
    # 分组:group by deptno
    # 表:emp
    select count(*),deptno from emp where sal > 1000 and sal < 4000 group by deptno;

```



## 1.3 万能公式

```mysql
select 结果 from 表 where 条件 group by 分组列 having 条件 order by 排序列 asc/desc limit m,n;

```























