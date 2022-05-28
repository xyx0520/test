# 1 进阶查询

## 1.1 子查询

- 定义
  - 一个sql语句中有2个及以上的select语句
  - 一个select语句的结果作为另一个select语句的条件

```mysql

# ******01 子查询*****************
# *****01.1单表子查询
# *****01.1.1单行子查询：子查询的结果返回的值只有一行，才可以用> = < >= <= !=号
# 语法:select 结果 from 表 where 列 >/</= (select语句)
# 案例:查询工资跟张三工资一样的员工信息,不显示张三
# 分析
# 1.查询工资="张三工资"的员工信息
# 结果:*
# 条件:sal = '张三工资' and ename != '张三'
# 表:emp
select * from emp where sal = '张三工资'and ename != '张三';  -- 伪代码

# 2.查询张三的工资
# 结果:sal
# 条件:ename = '张三'
# 表:emp
select sal from emp where ename = '张三';

# 3.组合最终语句
select * from emp where sal = (select sal from emp where ename = '张三')and ename != '张三';





#练习:查询工资比张三工资高的员工信息
# 1.查询sal>"张三的工资"的员工信息
# 结果:*
# 条件:sal > '张三的工资'
# 表:emp
select * from emp where sal > '张三的工资';

# 2.查询张三的工资
# 结果:sal
# 条件:ename = '张三'
# 表:emp
select sal from emp where ename = '张三';

# 3.组合最终语句
select * from emp where sal > (select sal from emp where ename = '张三');


#练习:查询工资比张三工资高,且跟张三是同一个部门的员工信息
# 1.查询sal>"张三的工资"and deptno = "张三的部门"的员工信息
# 结果:*
# 条件:sal>"张三的工资"and deptno = "张三的部门"
# 表:emp
select * from emp where sal>"张三的工资"and deptno = "张三的部门";

# 2.查询 张三的工资
# 结果:sal
# 条件:ename = '张三'
# 表:emp
select sal from emp where ename = '张三';

# 3.查询 张三的部门
# 结果:deptno
# 条件:ename = '张三'
# 表:emp
select deptno from emp where ename = '张三';

# 4.组合最终语句
select * from emp where sal>(select sal from emp where ename = '张三')
and deptno = (select deptno from emp where ename = '张三');

# ******01.1.2多行子查询：如果子查询的结果返回多行数据，此时可以in
# 语法:select 结果 from 表 where 列 in (select语句); 
# 案例:查询工资跟部门20员工工资相同的员工信息
# 分析
# 1.查询工资="部门20员工工资"的员工信息
# 结果:*
# 条件:sal = "部门20员工工资"
# 表:emp
select * from emp where sal = "部门20员工工资";

# 2.查询部门20员工的工资
# 结果:sal
# 条件:deptno = 20
# 表:emp
select sal from emp where deptno = 20;

# 3.组合成最终语句
select * from emp where sal in (select sal from emp where deptno = 20);


# 练习:查询岗位和10部门员工岗位一致的员工信息
# 1.查询job = '10部门员工岗位'的员工信息
# 结果:*
# 条件:job = '10部门员工岗位'
# 表emp:
select * from emp where job = '10部门员工岗位';
# 2.查询 10部门员工岗位
# 结果:job
# 条件:deptno = 10
# 表:emp
select job from emp where deptno = 10;
# 3 把1和2整合成最终的语句
select * from emp where job in (select job from emp where deptno = 10);

# 练习:查询部门编号和名字包含有'鲤'字部门编号一样的员工姓名
# 1.查询deptno = "名字包含有'鲤'字"的员工姓名
# 结果:ename
# 条件:deptno = "名字包含有'鲤'字"
# 表:emp
select ename from emp where deptno = "名字包含有'鲤'字";
# 2.查询 "名字包含有'鲤'字"的部门编号
# 结果:deptno
# 条件:ename like '%鲤%'
# 表:emp
select deptno from emp where ename like '%鲤%';
# 3.整合1和2步骤的语句
select ename from emp where deptno in (select deptno from emp where ename like '%鲤%');


# ********01.2多表子查询
# 语法:select 结果 from 表 where 多表共同列 in (select 多表共同列 from 表 后续有条件就加);
# 案例:查询工作地点在北京的员工信息
# 1.查询工作地点在北京的员工信息
# 结果:*
# 条件:工作地点在北京
# 表:emp
select * from emp where deptno in(工作地点在北京的共同列);

# 2.查询 工作地点在北京的共同列
# 结果:deptno
# 条件:loc = '北京'
# 表:dept
select deptno from dept where loc = '北京';
# 3.整合1和2语句
select * from emp where deptno in(select deptno from dept where loc = '北京');

#练习:查询工作地点在北京且工资高于2000的员工信息
# 1.查询    部门编号和工作地点在北京的部门编号一致 且 工资高于2000的  员工信息
# 结果:*
# 表:emp
# 条件:deptno in (工作地点在北京的部门编号) and sal>2000
select * from emp where deptno in (工作地点在北京的部门编号) and sal>2000;
# 2.查询 工作地点在北京的部门编号
# 结果:deptno
# 条件:loc = '北京'
# 表:dept
select deptno from dept where loc = '北京';
# 3.把1和2整合

select * from emp where deptno in (select deptno from dept where loc = '北京') and sal>2000;
#练习:查询工作地点在北京且工资高于张三工资的员工信息
# 1. 查询 两表共同列 in (工作地点在北京的两边共同列) and sal >(张三的工资) 的员工信息
# 结果:*
# 条件:两表共同列 in (工作地点在北京的两边共同列) and sal >(张三的工资)
# 表:emp
select * from emp where deptno in (工作地点在北京的两边共同列) and sal >(张三的工资);
# 2.查询 工作地点在北京的两边共同列 
# 结果:deptno
# 表:dept
# 条件:loc = '北京'
select deptno from dept where loc = '北京';
# 3.查询张三的工资
# 结果:sal
# 表:emp
# 条件:ename = '张三'
select sal from emp where ename = '张三';
# 4 整合1和2和3
select * from emp where deptno in (select deptno from dept where loc = '北京') 
and sal >(select sal from emp where ename = '张三');

#案例:查询工作地点为北京或者上海的员工信息
# 1.查询 共同列 in (工作地点为北京的共同列) or 共同列 in (工作地点在上海的共同列)  的员工信息
# 结果:*
# 条件:deptno in (工作地点为北京的共同列) or deptno in (工作地点在上海的共同列)
# 表:emp
select * from emp where deptno in (工作地点为北京的共同列) or deptno in (工作地点在上海的共同列);
#2 查询工作地点为北京的共同列
# 结果:deptno
# 条件:loc = '北京'
# 表:dept
select deptno from dept where loc = '北京';--10
# 3 查询工作地点在上海的共同列
# 结果:deptno
# 条件:loc = '上海'
# 表:dept
select deptno from dept where loc = '上海';--20
# 4 整合1和2和3
select * from emp where deptno in (select deptno from dept where loc = '北京') or
 deptno in (select deptno from dept where loc = '上海');
# 练习:查询姓名为三个字符的员工的部门名称
# 1.两边共同列 in (姓名为三个字符的员工的共同列) 的部门名称
# 结果:dname
# 条件:deptno in (姓名为三个字符的员工的共同列)
# 表:dept
select dname from dept where deptno in (姓名为三个字符的员工的共同列);
# 2.查询姓名为三个字符的员工的共同列
# 结果:deptno
# 条件:ename like '___'
# 表:emp
select deptno from emp where ename like '___';
# 3 整合1和2
select dname from dept where deptno in (select deptno from emp where ename like '___');


# 练习:查询有员工的部门名称
# 先分解:判断是否是用多表子查询
# 1 查询两表共同列 in (有员工的共同列) 的部门名称
# 结果:dname
# 条件:deptno in (有员工的共同列)
# 表:dept
select dname from dept where deptno in (有员工的共同列);
# 2 查询有员工的共同列
# 结果:deptno
# 条件:有员工
# 表:emp
select deptno from emp;
# 3整合 1和2
select dname from dept where deptno in (select deptno from emp);

# 练习:查询没有员工的部门名称
select dname from dept where deptno NOT in (select deptno from emp);

# 知识点1:   where sal is not null  /is null 

# 案例:查询比所有推销员工资都高的员工信息
# 1.查询工资> 所有推销员工资 的员工信息
# 结果:*
# 条件:sal > (所有推销员工资)
# 表:emp
select * from emp where sal > (所有推销员工资);
# 2.查询推销员的工资
# 结果:sal
# 条件:job = '推销员'
# 表:emp
select sal from emp where job = '推销员';
# 3整合1和2
select * from emp where sal > (select max(sal) from emp where job = '推销员');
# 1.工资大于推销员里最大的工资
# 2.使用all
select * from emp where sal > all(select sal from emp where job = '推销员');

# 练习1:查询高于其中某一个推销员工资的员工信息,使用2种方法写(any)
select * from emp where sal > (select min(sal) from emp where job = '推销员');
select * from emp where sal > any(select sal from emp where job = '推销员');
# 练习2:查询高于推销员最高工资的员工信息,使用2种方法写
# 练习3:查询低于推销员最低工资的员工信息,使用2种方法写 
select * from emp where sal < any(select sal from emp where job = '推销员');
select * from emp where sal < all(select sal from emp where job = '推销员');

```

## 1.2 组合查询

- 定义
  - 可以把两张表的数据加起来
  - 组合规则：列数相同，数据类型要相同
- 语法
  - select a,b from 表1 union select a,b from 表2
  - select a,b from 表1 union all select a,b from 表2

```mysql
# *****02 组合查询************
# 语法: sql语句 union sql语句
# 案例:把emp表的empno和ename这两列和dept表的deptno和loc放一张表里面
select empno,ename from emp union select deptno,loc from dept;
# 适用:两个表的列的数据类型一致
# union默认去重
# union all 不去重
# 案例:把dept表上下连接起来
select * from dept union all select * from dept;

```

## 1.3 多表查询

- 定义
  - 当查询的结果在多个表中时，需要从多个表中选择列进行输出

### 1.3.1 笛卡尔积查询

- 笛卡尔积查询： 表1,表2

```mysql
# *****03 笛卡尔积查询********
# 语法:select 结果 from 表1,表2,表3... where 表1.共同列=表2.共同列 and 表2.共同列= 表3.共同列...;
#	案例:查询员工姓名和其所在的部门名称
# 结果:ename,dname
# 表:emp,dept
# 条件:表1.共同列 = 表2.共同列
select ename,dname from emp e,dept d where e.deptno = d.deptno;

-- - 练习:查询工资大于2000的员工姓名和部门名称
# 结果:ename,dname
# 表:emp,dept
# 条件:emp.deptno = dept.deptno and sal > 2000
select ename,dname from emp,dept where emp.deptno = dept.deptno and sal > 2000;

-- - 练习:查询员工姓名,工资,工作地点
# 结果:ename,sal,loc 
# 表:emp,dept
# 条件:emp.deptno = dept.deptno
select ename,sal,loc from emp,dept where emp.deptno = dept.deptno;

-- - 练习:查询员工的姓名以及员工领导姓名
# 结果:e1.ename,e2.ename
# 表:emp e1,emp e2
# 条件:e1.mgr = e2.empno
select e1.ename,e2.ename from emp e1,emp e2 where e1.mgr = e2.empno;

-- - 练习:查询员工姓名以及员工领导姓名及员工的部门名称
# 结果:e1.ename,e2.ename,d.dname
# 表:emp e1,emp e2,dept d
# 条件:e1.mgr = e2.empno and e1.deptno = d.deptno
select e1.ename,e2.ename,d.dname from emp e1,emp e2,dept d where e1.mgr = e2.empno and e1.deptno = d.deptno;



# 案例:查询工资跟张三工资一样的员工信息,不显示张三
# 结果:*
# 表:emp,(张三的工资表)
# 条件:emp.sal = 表2.sal
select * from emp;
select * from emp where ename = '张三';
select e1.* from emp e1,(select * from emp where ename = '张三') e2 
where e1.sal = e2.sal and e1.ename != '张三';

# 练习:查询工资比张三工资高的员工信息
# 结果:*
# 表:emp e1,(select * from emp where ename='张三') e2
# 条件:e1.sal>e2.sal
select e1.* from emp e1,(select * from emp where ename='张三') e2 where e1.sal>e2.sal;
# 显示的结果在两个表里,emp和dept,结果:ename和dname(不能使用子查询)

# 练习:查询工作地点为北京或者上海的员工信息
# 结果:*
# 表:emp,dept
# 条件:emp.deptno = dept.deptno
# 思路1:把工作地点为北京或者上海这个条件放到表2中去
select emp.* from emp,(select * from dept where loc in ('北京','上海')) e2 where emp.deptno = e2.deptno;
# 思路2:把工作地点为北京或者上海这个条件放在两表笛卡尔积后再去筛选
select * from emp,dept where emp.deptno = dept.deptno and loc in ('北京','上海');
```





### 1.3.2 连接查询

- 分类
  - 内连接查询
    - select * from 表1 [inner] join 表2 on 条件;
    - 查询效率比笛卡尔积高
    - 把两张表内联，结果为符合条件的数据
  - 外连接查询
    - 左外联查询：A表左外联B表，符合条件的数据正常显示，A表中不符合查询条件的数据也显示出来，同时B表对应的列以空值替代
    - 语法:select 结果 from 表1 left join 表2 on 表1.共同列=表2.共同列 left join 表3 on 表2.共同列=表3.共同列;
    - 右外联查询：A表右外联B表，符合条件的数据正常显示，B表中不符合查询条件的数据也显示出来，同时A表对应的列以空值替代
      - 语法:select 结果 from 表1 rightjoin 表2 on 表1.共同列=表2.共同列 rightjoin 表3 on 表2.共同列=表3.共同列;

```mysql
# ****04 连接查询*****
# ****04.1 内连接*****
# 语法:select 结果 from 表1 join 表2 on 表1.共同列=表2.共同列; 
# 案例:查询姓刘的员工所在的部门名称
# 结果:dname
# 表:emp,dept
# 条件:ename like '刘%' and emp.deptno = dept.deptno
select * from emp join dept on emp.deptno = dept.deptno and ename like '刘%';
select * from emp,dept where emp.deptno = dept.deptno and ename like '刘%';
# 区别:
# 1语法不一样 笛卡尔积:表1,表2 筛选条件使用的是where  内连接:表1 join 表2 on
# 2内连接的查询速度比笛卡尔积快


# ****04.2 左外联*****
# 语法:select 结果 from 表1 left join 表2 on 条件 
# 案例:查询部门名称以及员工姓名，保留没有员工的部门名称
# 结果:dname,ename
# 表:emp,dept
# 条件:emp.deptno = dept.deptno
# 内连接
select * from emp join dept on emp.deptno = dept.deptno;
select * from dept left join emp on emp.deptno = dept.deptno;


# ****04.3 右外联*****
# 语法:select 结果 from 表1 right join 表2 on 条件 
# 案例:查询部门名称以及员工姓名，保留没有员工的部门名称
select * from emp right join dept on emp.deptno = dept.deptno;
```

- 练习题
  - 1.查询老师姓名、课程名称，没有课程的老师也显示出来
  - 2.查询学生姓名、课程编号，没有课程的学生姓名也显示出来
  - 3.查询学生姓名、课程名称、学生分数，只显示有课程和分数的信息
  - 4.查询学生姓名、课程名称、学生分数，没有课程的学生也显示出来

```mysql
-- 练习题
-- - 1.查询老师姓名、课程名称，没有课程的老师也显示出来
# 结果:tname,cname
# 表:teacher,course
# 条件:t.tid = c.tid
# 左连接
select tname,cname from teacher t left join course c on t.tid = c.tid;
# 右连接
select tname,cname from course c right join teacher t on t.tid = c.tid;

-- - 2.查询学生姓名、课程编号，没有课程的学生姓名也显示出来
# 结果:student.sname,sc.cid
# 表:student,sc
# 条件:student.sid = sc.sid
# 左连接
select * from student left join sc on student.sid = sc.sid;
# 右连接
select * from sc right join student on student.sid = sc.sid;
-- - 3.查询学生姓名、课程名称、学生分数，只显示有课程和分数的信息(三表)
# 结果:sname,cname,score
# 表:student,course,sc
# 条件:student.sid = sc.sid and sc.cid = course.cid
# 笛卡尔积
select sname,cname,score from student,course,sc where student.sid = sc.sid and sc.cid = course.cid;
# 内连接
select sname,cname,score from student join course join sc on student.sid = sc.sid and sc.cid = course.cid;
select sname,cname,score from student s join sc  on s.sid = sc.sid join course c on c.cid = sc.cid;

-- - 4.查询学生姓名、课程名称、学生分数，没有课程的学生也显示出来
select sname,cname,score from student s LEFT JOIN sc on s.sid = sc.sid LEFT JOIN course c on sc.cid = c.cid;
```

# 2 万能公式

```mysql
SELECT DISTINCT 结果列 FROM 表1 left/right JOIN 表2 ON 条件 WHERE 条件 GROUP BY 分组列 HAVING 条件 ORDER BY 排序列 LIMIT m,n;
```

在使用left/right join 时(内连接,on和where没有区别),on和where条件的区别如下:

1. on条件是在生成临时表时使用的条件，它不管on中的条件是否为真，都会返回左边表中的记录。
2. where条件是在临时表生成好后，再对临时表进行过滤的条件。这时已经没有left join的含义（left join是必须返回左边表的记录），条件不为真的就全部过滤掉。



```mysql
# 数据准备
SET FOREIGN_KEY_CHECKS=0;

-- ----------------------------
-- Table structure for course
-- ----------------------------
DROP TABLE IF EXISTS `course`;
CREATE TABLE `course` (
  `cid` int(11) NOT NULL,
  `cname` varchar(30) DEFAULT NULL,
  `tid` int(11) DEFAULT NULL,
  PRIMARY KEY (`cid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- ----------------------------
-- Records of course
-- ----------------------------
INSERT INTO `course` VALUES ('3001', '语文', '4');
INSERT INTO `course` VALUES ('3002', '数学', '2');
INSERT INTO `course` VALUES ('3003', '英语', '1');
INSERT INTO `course` VALUES ('3004', '物理', '3');

-- ----------------------------
-- Table structure for sc
-- ----------------------------
DROP TABLE IF EXISTS `sc`;
CREATE TABLE `sc` (
  `sid` int(11) NOT NULL,
  `cid` int(11) NOT NULL,
  `score` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- ----------------------------
-- Records of sc
-- ----------------------------
INSERT INTO `sc` VALUES ('101', '3001', '90');
INSERT INTO `sc` VALUES ('102', '3001', '85');
INSERT INTO `sc` VALUES ('103', '3001', '76');
INSERT INTO `sc` VALUES ('105', '3001', '87');
INSERT INTO `sc` VALUES ('106', '3001', '66');
INSERT INTO `sc` VALUES ('108', '3001', '96');
INSERT INTO `sc` VALUES ('101', '3002', '92');
INSERT INTO `sc` VALUES ('102', '3002', '81');
INSERT INTO `sc` VALUES ('103', '3002', '93');
INSERT INTO `sc` VALUES ('104', '3002', '73');
INSERT INTO `sc` VALUES ('105', '3002', '65');
INSERT INTO `sc` VALUES ('108', '3002', '96');
INSERT INTO `sc` VALUES ('101', '3003', '96');
INSERT INTO `sc` VALUES ('102', '3003', '85');
INSERT INTO `sc` VALUES ('103', '3003', '76');
INSERT INTO `sc` VALUES ('104', '3003', '63');
INSERT INTO `sc` VALUES ('105', '3003', '59');
INSERT INTO `sc` VALUES ('106', '3003', '56');
INSERT INTO `sc` VALUES ('107', '3003', '91');
INSERT INTO `sc` VALUES ('108', '3003', '86');
INSERT INTO `sc` VALUES ('101', '3004', '100');
INSERT INTO `sc` VALUES ('102', '3004', '83');
INSERT INTO `sc` VALUES ('103', '3004', '75');
INSERT INTO `sc` VALUES ('104', '3004', '69');
INSERT INTO `sc` VALUES ('105', '3004', '50');
INSERT INTO `sc` VALUES ('106', '3004', '52');
INSERT INTO `sc` VALUES ('107', '3004', '87');
INSERT INTO `sc` VALUES ('108', '3004', '78');

-- ----------------------------
-- Table structure for student
-- ----------------------------
DROP TABLE IF EXISTS `student`;
CREATE TABLE `student` (
  `sid` int(11) NOT NULL,
  `sname` varchar(30) DEFAULT NULL,
  `sage` int(11) DEFAULT NULL,
  `ssex` varchar(8) DEFAULT NULL,
  PRIMARY KEY (`sid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- ----------------------------
-- Records of student
-- ----------------------------
INSERT INTO `student` VALUES ('101', '龙大', '18', '男');
INSERT INTO `student` VALUES ('102', '熊二', '19', '男');
INSERT INTO `student` VALUES ('103', '张三', '18', '男');
INSERT INTO `student` VALUES ('104', '李四', '19', '女');
INSERT INTO `student` VALUES ('105', '王五', '20', '男');
INSERT INTO `student` VALUES ('106', '李华', '19', '男');
INSERT INTO `student` VALUES ('107', '李红', '19', '女');
INSERT INTO `student` VALUES ('108', '李明', '20', '男');
INSERT INTO `student` VALUES ('109', '贝贝', '19', '女');
INSERT INTO `student` VALUES ('110', '娜娜', '20', '女');
INSERT INTO `student` VALUES ('111', '赵五月', '23', '女');
INSERT INTO `student` VALUES ('112', '五月', '24', '男');
INSERT INTO `student` VALUES ('113', '五', '25', '男');

-- ----------------------------
-- Table structure for teacher
-- ----------------------------
DROP TABLE IF EXISTS `teacher`;
CREATE TABLE `teacher` (
  `tid` int(11) NOT NULL,
  `tname` varchar(30) DEFAULT NULL,
  PRIMARY KEY (`tid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- ----------------------------
-- Records of teacher
-- ----------------------------
INSERT INTO `teacher` VALUES ('1', '叶平');
INSERT INTO `teacher` VALUES ('2', '李龙');
INSERT INTO `teacher` VALUES ('3', '李逍遥');
INSERT INTO `teacher` VALUES ('4', '朱钊');
```



