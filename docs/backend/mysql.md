# mysql

### 地址:[mysql](https://www.bilibili.com/video/BV1Kr4y1i7ru/?spm_id_from=333.337.search-card.all.click&vd_source=e38cd951f2ee7bda48ec574f4e9ba363)

### mysql 常见命令

1. 显示所有数据库

```bash
show databases;
```

2. 进入某人数据库

```bash
use databases;
```

3. 查看数据库里的表

```bash
show tables;
```

4. 查看在某个数据库

```bash
slect database()
```

5. 创建一个表

```bash
create table info(id int name varchar(20));
```

6. 查看表结构

```bash
desc ifof(表名)

```
7. 查看数据

```bash
select * from info(表名)
```

8. 查看数据库版本

```bash
select version()
```

### mysql语法规范
1. 不区分大小写，但关建议关键字，表名，列名小写
2. 每条命令最好用分号结尾
3. 每条命令根据需要，可以进行缩进或换行

## DQL 查询语言
1. 查询表中单个字段

```bash
SELECT last_name (字段名) FROM employees;
```
2. 查询表中多个字段

```bash
SELECT last_name,salary,email from employees;
```
3. 查询表中所有字段

```bash
SELECT * FROM employees;
```
4. 查询常量值

```bash
SELECT 100;
```
5. 查询表过式

```bash
SELECT 100 * 98;
```
6. 查询函数

```bash
SELECT VERSION()
```

7. 起别名

```bash
SELECT 100%92 as 结果;
SELECT last_name as 姓,first_name as 名 FROM employees;
```
8. 去重

```bash
SELECT DISTINCT department_id from employees
```
9. 字符串的拼接

```bash
SELECT CONCAT(last_name,first_name) as 姓名 FROM employees;

```
### 条件查询
1. 按条件表过式筛选

```bash
SELECT * FROM employees WHERE salary > 12000
```

2. 按逻辑运算符进行筛选

```bash
SELECT last_name,salary,commission_pct FROM employees WHERE salary >=10000 AND salary <=20000;
SELECT * FROM employees WHERE NOT(department_id >=90 AND department_id <=110) OR salary >15000;
```

3. 模糊查询 like between and in is null is not null

```bash
SELECT * FROM employees WHERE last_name LIKE '%a%';

```
4. 查询两者之间between and 包含临界值，临界值的顺序不能错序

```bash
SELECT * FROM employees WHERE employee_id BETWEEN 100 AND 120;

```
5. in 判断某个字段的值是否属于in列表中的某一项

```bash
SELECT last_name,job_id FROM employees WHERE job_id IN('IT_PROT','AD_VP','AD_PRES');
```

6. is null  = 或<>不能用于判断null值

```bash
SELECT last_name,commission_pct FROM employees WHERE commission_pct IS NULL
```
### 排序查询

1. 从高到低进行排序

```bash
SELECT * FROM employees ORDER BY salary DESC;
```
2. 排序+筛选

```bash
SELECT * FROM employees WHERE department_id >=90 ORDER BY hiredate ASC
```
3. 按字节进行排序

```bash
SELECT LENGTH(last_name) last_name,salary FROM employees ORDER BY LENGTH(last_name) DESC;

```
4. 模糊查询排序

```bash
SELECT *,LENGTH(email) FROM employees WHERE email LIKE '%e%' ORDER BY LENGTH(email) DESC, department_id ASC;
```

### 字符函数

1. 获取字符串的字节个数

```bash
SELECT LENGTH("hello world");
```

2. 拼接字符口串

```bash
SELECT CONCAT(last_name,'_',first_name) as 姓名 FROM employees;
```
3. upper,lower 将字符串变大写，小写

```bash 
SELECT CONCAT(UPPER(last_name),UPPER(first_name)) as 姓名 FROM employees;
 
```
4. substr 截取从指定索引处后面的所有字符

```bash
SELECT SUBSTR("李莫悉爱上了陆展元",7) as out_put;
SELECT SUBSTR("李莫悉爱上了陆展元",1,3) as out_put;
```
5. instr 返回子串第一次出现的索引，如果找不到返回0

```bash
SELECT INSTR('杨不悔爱上了六侠','六侠') as out_put;
```
6. trim 
```

```
7. lpad 用指定的字符实现左填充指定长度

```bash
SELECT LPAD("刘德华",10,"*") as out_put;

```
8. rpad 用指定的字符实现右填充指定的长度

```bash
SELECT RPAD("刘德华",10,"*") as out_put;
```
9. replace 替换

```bash
SELECT REPLACE("张无忌爱上周芷若","周芷若","赵敏") as out_put;
 
```
### 常用数学函当我

1. round 四舍五入
```
SELECT ROUND(1.55) as out_put;
 
```
2. ceil 向上取整

```bash
SELECT CEIL(1.01) as out_put;
```
3. floor 向下取整

```bash
SELECT FLOOR(1.65) as out_out;
```
4. truncate 截断

```bash
SELECT TRUNCATE(1.65,1) as out_put;
```
5. mod 取余

```bash
SELECT MOD(10,3) as out_put;
```
### 日期函数
1. now 返回当前系统日期+时间

```bash
SELECT NOW() as out_put;
```

2. curdate 返回当前系统日期，不包含时间

```bash
SELECT CURDATE();
```

3. curtime 返回当前日间，不包含日期
```bash
SELECT curtime();
```
4. 指定返回年，月，日，时 ，分，秒

```bash
SELECT YEAR(NOW()) as out_put;
```
### 流程控制函数
1. if 函数

```bash
SELECT IF(10 > 5,'大','小');
SELECT last_name,commission_pct,IF(commission_pct IS NULL,'没奖金,呵呵','有奖金,嘻嘻')  备注 FROM employees;
```

2. case 函数

```bash
SELECT salary 原始工资,department_id,
CASE department_id
	WHEN 20 THEN salary * 1.1
	WHEN 40 THEN salary * 1.2
	WHEN 50 THEN salary * 1.3
	ELSE salary
END AS 新工资 FROM employees;

```

### 分组函数
1. sum求合

```bash
SELECT SUM(salary) FROM employees;
```
2. avg求平均值

```bash
SELECT AVG(salary) FROM employees;
```
3. distinct 去重

```bash
SELECT SUM(DISTINCT salary) FROM employees;
```

4. count 统计
```bash
SELECT COUNT(DISTINCT salary) FROM employees;
```
5. 求最大值，最小值，总合

```bash
SELECT MAX(salary) as 最大值,MIN(salary) as 最小值,SUM(salary) as 总合 from employees;
```

6. 求两个时间相差的天数
```bash
SELECT DATEDIFF(MAX(hiredate),MIN(hiredate)) as 差异 FROM employees;
```
7. 统计某个部门id的个数

```bash
SELECT COUNT(*) 个数 FROM employees WHERE department_id = 90;
```
### group by函数

1. 查询每个工种的最高工资

```bash
SELECT MAX(salary),job_id FROM employees GROUP BY job_id;
```

2. 查询每个位置上的部门数
```bash
SELECT COUNT(*),location_id FROM departments GROUP BY location_id;
 
```

3. 查询每个部门的平均工资

```bash
SELECT AVG(salary),department_id FROM employees GROUP BY department_id;
```

4. 查询有奖金的每个领导手下员工的最高工资
```bash
SELECT MAX(salary),manager_id FROM employees WHERE commission_pct IS NOT NULL GROUP BY manager_id;
```
5. 查询每个部门员工数大于2的

```bash
SELECT COUNT(*),department_id FROM employees GROUP BY department_id HAVING COUNT(*) > 2
```
### join连接查询

1. 查询员工名对应的部门名

```bash
SELECT last_name,department_name FROM employees,departments WHERE employees.department_id = departments.department_id;

```
2. 查询员工名，工种号，工种名

```bash
SELECT last_name,employees.job_id,job_title FROM employees,jobs WHERE employees.job_id = jobs.job_id;

```
3. 查询有奖金的员工名，部门名

```bash
SELECT last_name,department_name,commission_pct FROM employees e,departments d WHERE e.department_id = d.department_id AND e.commission_pct IS NOT NULL;
 
```
4. 查询城市名第二个字符为o的部门名和城市名

```bash
SELECT department_name,city FROM departments d,locations l WHERE d.location_id = l.location_id AND city LIKE '_o%';
```
5. 查询每个城市的部门个数

```bash
SELECT COUNT(*) AS 个数,city FROM departments d,locations l WHERE d.location_id = l.location_id GROUP BY city;
```
6. 查询每个工种的工种名和员工个数，并且按员工个数降序

```bash
SELECT job_title,COUNT(*) FROM employees e,jobs j WHERE e.job_id = j.job_id GROUP BY job_title ORDER BY COUNT(*) DESC;
 
```

7. 等值链查询员工名，部门名
```bash
SELECT last_name,department_name FROM employees e INNER JOIN departments d ON e.department_id = d.department_id;

```
8. 查询名字中包含e的员工名和工种名 
```bash
SELECT last_name,job_title FROM employees e INNER JOIN jobs j ON e.job_id = j.job_id WHERE e.last_name LIKE '%e%';

```

9. 查询部门数大于3的城市名和部门数
```bash
SELECT city,COUNT(*) AS 部门个数 FROM departments AS d INNER JOIN locations AS l ON d.location_id = l.location_id GROUP BY city HAVING COUNT(*) > 3;

```
### 日期与时间
1. 
```bash
SELECT CURDATE(),CURRENT_DATE(), CURTIME(), NOW(),SYSDATE(),UTC_DATE(),UTC_TIME() FROM DUAL;

```
2. 日期与时间cho
```bash
SELECT UNIX_TIMESTAMP();
SELECT FROM_UNIXTIME(1702247160)
```





### 子查询 

1. 标是子查询 查询工资比Abel高的

```bash
SELECT * FROM employees WHERE salary > (SELECT salary FROM employees WHERE last_name = "Abel");
```

2. 返回公司工资最低的员工的last_name,job_id和salary

```bash
SELECT last_name,job_id,salary FROM employees
WHERE salary = (SELECT MIN(salary) FROM employees);
```

3. 
```bash
SELECT MIN(salary),department_id FROM employees 
GROUP BY department_id 
HAVING MIN(salary) > (SELECT MIN(salary) FROM employees WHERE department_id = 50);
```

4. 行子查询
```

```
### 分页查询
1. 查询前5条员工信息 
```bash
SELECT * FROM employees LIMIT 0, 5;
```
2. 查询第11条到第25条

```bash
SELECT * FROM employees LIMIT 10, 15;
```
## DDL 语句
### 插入语法
1. 插入的值的类型要与列的类型兼容或一致

```bash
INSERT INTO beauty(id,`name`,sex,borndate,phone,photo,boyfriend_id) VALUES(13,'刘德华','男','1789-4-23','15083356190',NULL,2)
```

2. 插入方式2

```bash
INSERT INTO beauty SET id = 15,`name` = "刘涛", borndate = "1978-09-10", phone = "15082256191"
```
### 修改语法

1. 修改单表的记录

```bash
UPDATE beauty SET `name` = "阿涛" WHERE id = 15
UPDATE beauty SET phone = "15083356190" WHERE `name` LIKE "阿%"
```

### 删除语语
1. 单表的删除
```bash
DELETE FROM beauty WHERE id = 15;

```

2. 删除手机号为9结层的用户信息
```bash
DELETE FROM beauty WHERE phone LIKE '%9';
```

3. 多表连接删除

```bash
DELETE b FROM beauty b INNER JOIN boys bo NO b.boyfriend_id = bo.id WHERE bo.boyName = "张无忌";
```
4. 创建表

```bash
CREATE TABLE my_employess(
	id INT(10),
	first_name VARCHAR(10),
	last_name VARCHAR(10),
	salary DOUBLE(10,2)
);

```
## DDL 数据定义语言
1. 创建数据库

```bash
CREATE DATABASE books;
CREATE DATABASE IN NOT EXISTS books;
```
2. 删除库

```bash
DROP DATABASE books;
```
3. 创建表

```bash
CREATE TABLE book(
	id INT,
	bname VARCHAR(25),
	price DOUBLE,
	author VARCHAR(20)
);
```
4. 修改表的字段名

```bash
ALTER TABLE book CHANGE COLUMN author pub_author  VARCHAR(20);

```
5. 添加表的新列

```bash
ALTER TABLE book ADD COLUMN salary DOUBLE;

```
6. 删除表的一列

```bash
ALTER TABLE book DROP COLUMN salary;
```
7. 修改表名

```bash
ALTER TABLE book RENAME TO book_info;

```
8. 表的删除

```bash
DROP TABLE book_info;
```

9. 复制表的结构

```bash
CREATE TABLE copy LIKE book;
```
10. 复制表的结构与数据

```bash
CREATE TABLE copy2 SELECT * FROM book;

```
### sql的执行过程
```bash
form ... -> on -> (left/ right join) -> where -> group by -> having -> 
select -> distinct -> order by -> limit

```


### 子查询要重看
```bash
https://www.bilibili.com/video/BV1iq4y1u7vj?p=44&spm_id_from=pageDriver&vd_source=e38cd951f2ee7bda48ec574f4e9ba363
```



## mysql高级

### Linux安装mysql
1. 下载mysql的repo源

```bash
$ wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
```
2. 安装mysql-community-release-el7-5.noarch.rpm包

```bash
sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm
```
- 安装这个包后，会获得两个mysql的yum repo源：/etc/yum.repos.d/mysql-community.repo，/etc/yum.repos.d/mysql-community-source.repo。

3. 安装mysql
```bash
sudo yum install mysql-server
```
- 根据步骤安装就可以了，不过安装完成后，没有密码，需要重置密码。

4. 重置密码,重置密码前，首先要登录

```bash
mysql -u root
```
- 登录时有可能报这样的错：ERROR 2002 (HY000): Can‘t connect to local MySQL server through socket ‘/var/lib/mysql/mysql.sock‘ (2)，原因是/var/lib/mysql的访问权限问题。下面的命令把/var/lib/mysql的拥有者改为当前用户：

```bash
sudo chown -R openscanner:openscanner /var/lib/mysql
```
- 假如出现
- chown: invalid user: ‘openscanner:openscanner’
```bash

chown root /var/lib/mysql/
```

5. 重启服务
```bash
service mysqld restar
```

6. 设置mysql密码
```bash
/usr/bin/mysqladmin -u root password tungee1024Zhang
```

### mysql安装位置

1. 查看mysql安装位置

```bash
ps -ef | grep mysql 
```

CREATE DATABASE iblog CHARACTER SET utf8 COLLATE utf8_general_ci;


## mysql高级
### mysql字符集
1. 查看mysql字符集

```bash
show variables like '%character%';
```
2. 设置为utf8

```bash
vim /etc/my.cnf
character_set_server=utf8
```

3. 重启mysql

```bash
systemctl restart mysqld.service
```

### 用户管理

1. 创建用户

```bash
CREATE USER 'zhangsan' IDENTIFIED by 'abc123';
```
2. 修改密码

```bash
ALTER USER 'zhangdezhi' IDENTIFIED by 'tungee1024Zhang';
```




<!-- tungee1024Zhang -->

<!-- 
docker run -d --name mysql -e MYSQL_ROOT_PASSWORD=12356 -p 3306:3306 mysql:latest


docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=<password> -d mysql



[last](https://www.bilibili.com/video/BV1iq4y1u7vj?p=109&vd_source=e38cd951f2ee7bda48ec574f4e9ba363)



docker run -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 \
-v /etc/mysql/data:/var/lib/mysql \
-v /etc/mysql/conf.d:/etc/mysql/conf.d \
-v /etc/mysql/logs:/logs\
--name mysql \
-d mysql:latest -->
