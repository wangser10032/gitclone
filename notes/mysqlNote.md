### MySQL数据库

关系型数据库（RDBMS）：建立在关系模型基础上，由多张相互连接的二维表组成的数据库

MySQL启动：net start mysql80

cmd命令行：mysql [-h 127.0.01] [-P 3306] -u root -p

### SQl分类

DDL：  Data Definition Language 数据定义语言，定义数据库对象（数据库，表，字段）

DML： Data Manipulation Language 数据操作语言，增删改

DQL： Data Query Language 数据查询语言，查询数据库中表的记录

DCL： Data Control Language 数据控制语言，创建数据库用户，控制数据库访问权限

### 语法

sql语句不区分大小写；

语句以 ； 结尾；

字符串类型名字为varchar(index) index为长度；

### mysql图形化界面工具

Datagrip

### DDL

```mysql
--数据库查询操作


CREATE DATABASE [IF NOT EXISTS] 数据库名 [DEFAULT CHARSET字符集] [ COLLATE]; --utf8mb4支持四个字符，utf8只支持3个字符

USE 数据库名;



SHOW DATABASES; --查询所有数据库
SELECT DATABASE(); --查询当前数据库（名）
show tables;--查询当前数据库的所有表
show create table 表名; --查询建表语句
desc 表名;--查询表


--DDL 创建操作

create table 表名(
	字段1 字段1类型 comment [字段注释],
    字段2 字段2类型 comment [字段注释],
    字段3 字段3类型 comment [字段注释],
    字段4 字段4类型 comment [字段注释] --最后一个不加,
)[表注释] --comment添加注释
--例子
create table iscat(
   id int comment '编号',
   name varchar(50) comment '姓名',
   age int comment '年龄',
   gender varchar(1) comment '性别'
) comment '用户表';

 --DDL 表操作 修改
 alter table 表名 ADD 字段名 类型(长度) [comment 注释][约束]   --添加字段
 --例子
 alter table iscat add nickname varchar(20) comment '昵称'
 -- 修改表名
 alter table 表名 rename to 新表名;
 -- 修改数据类型
 alter table 表名 modify 字段名 新数据类型(长度);
 -- 修改字段名和数据类型
 alter table 表名 change 旧字段名 新字段名 类型(长度) [comment 注释][约束];
 --例子
 alter table iscat    change nickname username varchar(30) ;
 
 --DDL 删除
alter table 表名 drop 字段名; --删除某个表字段
DROP DATABASE [IF EXISTS] 数据库名; --删除数据库
truncate table 表名; --删除表名并且重新创建
```

![Screenshot_20230828_195030_tv.danmaku.bilibilihd](D:\Typora\notes\mysqlNote.assets\Screenshot_20230828_195030_tv.danmaku.bilibilihd-1693224876836-1.jpg)



### DML 数据操作语言，增删改

添加数据 insert

修改数据 update

删除数据 delete

```mysql
DML
1.指定字段添加数据
insert into 表名 ( 字段名1，2，3 ), qwe qwe qe values ( 值1，2，3) ;
2.给全部字段添加数据
insert into 表名 values(值1，2，3);       
3.批量添加数据
insert into bm (zd1,2,3,...) into values ((z1,...)(z2,...).....);
insert into bm into values (z1,...),(z2,...).....;--以此(所有)数据
--插入数据时，字段顺序应该一一对应
--字符串和日期型数据应该包含在引号中。
select * from 表名;查询语句

--修改数据
update bm set 字段名1=值1,字段名2=值2，字段名3=值3 where 条件;

--删除数据
delect from bm where 条件;
```

### DQL 数据查询语言

#### DQl语法-编写顺序

```mysql
select 字段 from 表名 
where 条件 
group by 分组字段列表 
having分组后条件列表 
order by 排序字段列表 
limit 分页参数
```

#### 基本查询

```sql
--查询多个字段
select zd1,zd2,zd3... from bm;
select * from bm;--查询表中所有字段
--设置别名
select 字段1 [as 别名1] ... from 表名; -- as可以省略
--as 别名指的是将查询结果的字段名改为别名显得更加可读
--去除重复记录，作用类型同上
select distinct zd from 表名;
```



#### 条件查询

```sql
select 字段列表 from 表名 where 条件列表;
```

![Screenshot_20230828_215515_tv.danmaku.bili](D:\Typora\notes\mysqlNote.assets\Screenshot_20230828_215515_tv.danmaku.bili.jpg)

```sql
select * from iscat where zd in(12,23,34);--iscat中zd为12，23，34的信息
select * from iscat where zd like '__'; --iscat中zd为两个字符的信息
select * from iscat where zd like '%X'; --查询身份证最后一位是X的员工信息
select * from iscat where zd like '_________________X';--作用同上;
```

#### 聚合函数

![{D79B907E-0A4D-4499-8AE6-E813E65FD219}](D:\Typora\notes\mysqlNote.assets\{D79B907E-0A4D-4499-8AE6-E813E65FD219}.png)

```sql
select count(id) from iscat; --查询id的总数据量
--null不参加，*更适合
select avg(age) from iscat; --查看平均年龄  
select sum(age) from iscat where workaddress = '西安'; -- 西安所有人年龄之和
```

#### 分组查询

```sql
select 字段列表 from 表名 [where 条件 ] group by 分组字段名 [having 分组后过滤条件];
--where对分组之前进行过滤，having对分组的结果进行过滤
--where不能进行聚合函数运算，而having可以使用;
select gender,count(*) from emp group by gender; --根据性别分组并统计男性员工和女性员工的数量
--执行顺序 where > 聚合函数 > having
```

#### 排序查询 

```sql
select 字段列表 from 表名 order by 字段1 排序方式1,字段2 排序方式2;
```

排序方式：  ASC 升序(默认)，DESC降序。



#### 分页查询

```sql
select 字段列表 from 表名 limit 起始索引,查询记录数;
-- 起始索引从零开始，起始索引 = （查询页码 - 1） * 每页记录数;
-- 分页查询是数据库的方言，mysql中是limit，其他不一定;
-- 第一页数据可以省略起始索引;

-- 例子
selec * from iscat limit 0,10; -- 查询第一页数据每一页展示10条
```

#### DQL执行顺序

![{7F89A385-C63E-4456-94EC-8DF0A2428D0B}](D:\Typora\notes\mysqlNote.assets\{7F89A385-C63E-4456-94EC-8DF0A2428D0B}.png)

#### DCL 数据控制语言

```sql
1.查询用户
use mysql;
select * from user;
2.创建用户
create user '用户名'@'主机名' identified by '密码'; --主机名用%表示任意主机都可以显示
3.修改用户密码
alter user '用户名'@'主机名' identified with mysql_native_password by '新密码';
4.删除用户
drop user '用户名'@'主机名';
```

DCL权限控制

![{2A7DF9EC-50B7-4cd7-A2B4-5908A4C86BA2}](D:\Typora\notes\mysqlNote.assets\{2A7DF9EC-50B7-4cd7-A2B4-5908A4C86BA2}.png)

1.查询条件

```sql
show grants for '用户名'@'主机名'; --查询用户所拥有的权限
```

2.授予权限

```sql
grant 权限列表 on 数据库名.表名 to '用户名'@'主机名';
```

3.撤销权限

```sql
revoke 权限列表 on 数据库名.表名 from '用户名'@'主机名';
```

```sql
--多个权限之间使用逗号分隔
--授权时，数据库名和表名都可以使用*进行通配，代表所有。
```

### 约束

作用域表中字段上的规则，用于限制表中的数据

主键约束: primary key 实现主键自动增长，mysql数据库中使用auto_increment

非空约束: not null

唯一约束: unique

默认约束: default

检查约束: check

外键约束: foreign key

![{6F366F11-0216-4ec4-A32D-64321BA119BE}](D:\Typora\notes\mysqlNote.assets\{6F366F11-0216-4ec4-A32D-64321BA119BE}.png)

外键约束

外键让两张表的数据直接建立连接，保证数据的一致性和完整性![{9D94328D-7804-44e8-B284-68AAF22A8AE1}](D:\Typora\notes\mysqlNote.assets\{9D94328D-7804-44e8-B284-68AAF22A8AE1}.png)

```sql
create table 表名(
	字段名 数据类型
    ...
    [constraint] [外键名称] foreign key(外键字段名) references 主表 (主表列名)
    --外键名称自由定义 该表外键字段名
);
alter table 表名 add constraint 外键名称 foreign key(外键列名/字段) references 主表表名(主表列名)
--例子
alter table emp add constraint fk_enp_id foreign key (dept_id) references dept(id) ;
--fk_mep_id是外键别名
--datagrip中黄色钥匙表示主键，蓝色钥匙表示外键
--删除外键
alter table emp drop foreign key fk_emp_dept_id;
```

#### 删除/更新行为

no action/restrict: 更新/删除父表时，检查是否有对应的外键，有则不允许更新/删除

cascade:  更新/删除父表时检查是否有外键，有则直接更新/删除外键在子表中的记录

set null:   当在父表中删除记录时，首先检查该记录是否有对应外键，如果有则设置子表中该外键值为nul

set default 父表有变更时将外键设置成一个默认的值。

子表关联父表

```sql
alter table 表名 add constraint 外键名称 foreign key (外键字段) references 主表名(主表字段)
on update cascade on delete cascade;
```

constraint 约束，限制 

cascade 级联

```sql
--alter table emp add constraint fk_enp_id foreign key (dept_id) references dept(id);
```

###  多表查询

#### 内连接

两个或者多个满足条件的表(NO NULL)合并在一起，不满足的排除在外，包括显式内连接和隐式内连接

```sql
SELECT employees.name, departments.department_name #select表示检索数据的关键字
FROM employees  #from+表名 检索数据表或者视图的名称
JOIN departments ON employees.department_id = departments.id; 
#join on是将多个数据表合并在一起的关键字，join表示希望连接那些数据表 ，on用来指示连接条件
#上例表示将employees和departments连接在一起，要求是按照employees.department_id = departments.id进行连接
```

显式内连接如上

隐式内连接如下

```sql
SELECT employees.name, departments.department_name
FROM employees, departments
WHERE employees.department_id = departments.id;
#where表示连接条件
```

区别在于FROM和WHERE关键字后面的

#### 外连接

将两个或者多个表中行连接在一起，同时包括满足连接条件和不满足条件的行,包括左外，右外和全外。

```sql
SELECT employees.name, departments.department_name
FROM employees
left JOIN departments ON employees.department_id = departments.id;
```

左外连接：返回左表所有的行和与之匹配右边的行，找不到填充为NULL，如上

右外连接；返回右表所有的行和与之匹配左边的行

```sql
SELECT employees.name, departments.department_name
FROM employees
right JOIN departments ON employees.department_id = departments.id;
```

全外连接：返回所有的行，但是mysql不满足圈外支持语法

#### 自连接

```sql
SELECT e1.name AS employee_name, e2.name AS manager_name
FROM employees e1
JOIN employees e2 ON e1.manager_id = e2.id;
#自连接一定要使用别名
#select之后使用别名要求加关键字 AS ，from之后空格＋别名即可。
```

#### 联合查询

关键字：union，union all，union表示将结果去重，union表示将所有的结果全部写出

union查询就是把多次查询的结果合并在一起，形成一个新的查询结果

对于联合查询的多张表的列数必须保持一致，且字段类型也保持一致

```sql
SELECT name, position
FROM employees
UNION #将结果去重,union all直接将所有结果显示
SELECT name, position
FROM contractors;
```

#### 子查询

子查询（Subquery），也被称为嵌套查询，是一种 SQL 查询的结构，其中一个查询嵌套在另一个查询内部。子查询可以在主查询的 WHERE、FROM 或 HAVING 子句中使用，用于从一个查询中检索数据，并将其作为另一个查询的条件、源表或计算的一部分。

```sql
#将2023年之前的所有用户全部
SELECT customer_name
FROM customers
WHERE customer_id IN (
    SELECT customer_id
    FROM orders
    WHERE order_date < '2023-01-01'
);
```

```sql
#查询所有的部门信息，并统计部门的员工人数
#部门信息为dept表，员工信息为emp表
select count(*) from emp where dept_id = 1;
select d.id,d.name,(select count(*) from emp where dept_id =  d.id) from dept d;  
```



##### 标量子查询

返回结果是单个值

##### 列子查询

子查询返回结果是多行，常见操作符是in, not in, any==some , all

标量子查询和列子查询都是 = 号

![{70B745CA-8675-4ccb-818A-4D7D86ADAAA1}](D:\Typora\notes\mysqlNote.assets\{70B745CA-8675-4ccb-818A-4D7D86ADAAA1}.png)

```sql
select id from emp where name = '市场部' or '销售部';
select * from emp where id in ...;#...由上得出
select * from emp where id in (
    select id 
    from emp
    where name = '市场部', '销售部'
);
#查询所有员工工资大于财务部所有人工资的部分员工
select * from emp where salary > all (select salary from emp where id =(select id from emp where name = '财务部'))
#如果是大于财务部任意一人时将all改为any即可
```

##### 行子查询

子查询返回的结果是一行(可以是多列)，行字查询是 ( 字段列表) =  

```sql
#错误示范select name,where salary = (select salary from emp where name = '张无忌') and name = ;
```

```sql
#查询与'张无忌'的薪资及直属领导相同的员工信息
select * from emp where (salary,managerid) = (select salary,managerid from emp where name = '张无忌');
```

##### 表子查询

子查询返回的结果是表，表子查询是 (字段列表) in

```sql
#查询与'宋远桥''张无忌'的薪资及直属领导相同的员工信息，--满足一个条件
select * from emp where (salary,managerid) in (select salary,managerid from emp where name = '张无忌');
```

```sql
#查询入职日期在'2006-01-01'之后的员工信息，及其部门信息,员工信息在一个表emp，部门信息在另外一个表dept
select e.*,d.* from (select * from emp where entrydate > 2006-01-01 ) e left join dept d on e.dept_id = d.id;
```

