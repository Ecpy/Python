## MySQL

### 进入MySQL : 
alias mysql=/usr/local/mysql/bin/mysql
mysql -u root -p

- 指令

	- MySQL内的数据库 database

		- 增

			- 创建数据库

				- create database if not exists 数据库名称 default charset utf-8;
				- creat database Nane;

		- 删

			- 删除数据库

				- drop database 数据库名称;

		- 查

			- 查看所有数据库

				- show databases;

		- 改

			- 切换到某数据库

				- use 数据库名称;

			- 属性修改

				- alter database ...

	- 数据库内的数据表 table

		- 增

			- 创建数据表并初始表字段

				- create table if not exists 数据表名称(key1 varchar(20), key2 varchar(10),...);

					- `user_id` INT UNSIGNED AUTO_INCREMENT,
PRIMARY KEY ( `user_id` )

			- 添加字段

				- alter table 数据表名称 add key2 varchar(20) after PeriodID;

		- 删

			- 删除数据表

				- drop table if exists 数据表名称;

			- 删除列

				- ALTER TABLE <表名> DROP <字段名>;

		- 查

			- 查看所有数据表

				- show tables;

		- 改

			- 属性修改

				- alter table ...

					- 修改表名

						- alter table old rename to new;

					- 修改表字符集

						- alter table tableName character set utf-8 

					- 添加数据列

						- alter table 数据表名称 add key2 varchar(20) after PeriodID;

							- first   # 定位到首列

					- 修改列名

						- alter table tableName change old newKey data; # data is type 

					- 修改列数据类型

						- alter table tableName modify key newType;

	- 数据表内的数据 

		- 增

			- 插入数据

				- insert into 表名 (字段1, ……) values (值1, ……);

		- 删

			- 删除全部数据

				- delete from tableName

			- 删除符合条件的数据

				- delete from 表名 where 字段=值;

			- 删除列

				- ALTER TABLE <表名> DROP <字段名>;

		- 查

			- 查看字段(表头)属性

				- desc 数据表名称;

			- 查询数据

				- SELECT * FROM 表名;
				- SELECT 列1, 列2, ... FROM 表名;
				- select * from 表名 where 字段 = 值;
				- 查寻并去重

					- SELECT DISTINCT 列1, 列2, ... FROM 表名;
					- 统计不同值的数量

						- SELECT COUNT(DISTINCT age) FROM t_users;
						- select count(distinct STATION_TYPE, Wipasx_Scenario) from stationRowDataTable_2023_01_11 where STATION_TYPE="CELL-S1"

			- 从小到大排序查询

				- select * from IN_PERIOD order by PeriodID ASC;

			- 从大到小排序查询

				- select * from IN_PERIOD order by PeriodID DESC;

			- 正则表达式

				- ^

					- 匹配文本的开始字符	‘^b’ 匹配以字母 b 开头 的字符串	book、big、banana、 bike

				- $

					- 匹配文本的结束字符	'st$’ 匹配以 st 结尾的字 符串	test、resist、persist

				- .

					- 匹配任何单个字符	'b.t’ 匹配任何 b 和 t 之间有一个字符	bit、bat、but、bite

				- *	

					- 匹配零个或多个在它前面的字 符	'f*n’ 匹配字符 n 前面有 任意个字符 f	fn、fan、faan、abcn

				- +

					- 匹配前面的字符 1 次或多次	'ba+’ 匹配以 b 开头，后 面至少紧跟一个 a	ba、bay、bare、battle

				- <字符串>

					- <字符串>	匹配包含指定字符的文本	'fa’	fan、afa、faad

				- [字符集合]	

					- 匹配字符集合中的任何一个字 符	'[xz]'匹配 x 或者 z	dizzy、zebra、x-ray、 extra

				- [^]

					- 匹配不在括号中的任何字符	'[^abc]’ 匹配任何不包 含 a、b 或 c 的字符串	desk、fox、f8ke

				- 字符串{n,}

					- 匹配前面的字符串至少 n 次	b{2} 匹配 2 个或更多 的 b	bbb、 bbbb、 bbbbbbb

				- 字符串 {n,m}

					- 匹配前面的字符串至少 n 次， 至多 m 次	b{2,4} 匹配最少 2 个， 最多 4 个 b	bbb、 bbbb

		- 改

			- 更新数据

				- update 表名 字段=值,…,字段n=值n where 字段=值;
				- update IN_PERIOD set TimePoint = "0:00" where PeriodID = 2;

	- 关键词/语句

		- WHERE 条件语句

			- WHERE 语句用于过滤数据，查询符合我们要求的数据

				- SELECT 列1, 列2, ...FROM 表名 WHERE 条件语句;

					- 单条件语句

						- =
						- >  >=
						- <   <=
						- <>   !=

							- "where SN not in ('NA') and CFG not in ('UNKNOWN')

						- between

							-  WHERE age BETWEEN 12 AND 13;

						- like

							- 正则表达式

								- WHERE username LIKE 'J%'; /*J开头的username*/

						- in

							- WHERE username IN ('Li','Jhon');

					- 多条件语句

						- and

							- WHERE 条件1 AND 条件2 AND 条件3 ...;

						- or

							-  WHERE 条件1 OR 条件2 OR 条件3 ...;

						- not

							- WHERE NOT 条件;

				- SELECT 课程号,AVG(成绩) FROM score GROUP BY 课程号 HAVING AVG(成绩)>=80;

		- ORDER BY 排序

			- SELECT 列1, 列2, ... FROM 表名 ORDER BY 列1, 列2, ... ASC|DESC;    # abc小到大,desc大到小

				- ORDER BY age DESC , username ASC;

		- create 创建语句
		- drop 抹除语句
		- delete 删除语句
		- select 查询语句
		- update 篡改语句
		- insert into 数据插入语句
		- alter 修改语句

	- MySQL设置

		- 退出mysql

			- exit

		- 用户操作

			-  新建用户

				- -- 创建了一个名为：mybatis 密码为：123 的用户
create user 'mybatis'@'localhost' identified by '123';

					- 如果想远程登录的话，将"localhost"改为"%"

			- 查询用户

				- select host,user from mysql.user;

			- 删除用户

				- -- 删除用户“mybatis”
drop user mybatis@localhost;
				- -- 若创建的用户允许任何电脑登陆，删除用户如下
drop user mybatis@'%';

			-  更改密码

				- -- 修改用户“mybatis”的密码为“1234”
alter user 'mybatis'@'localhost' identified with mysql_native_password by '1234';
-- 刷新
flush privileges;

			- 用户分配权限

				- -- 授予用户 mybatis 通过外网IP对数据库“mybatis_db”的全部权限
grant all privileges on mybatis_db.* to 'mybatis'@'%';
--刷新权限
flush privileges; 
-- 授予用户“mybatis”通过外网IP对于该数据库“mybatis_db”中表的创建、修改、删除权限,以及表数据的增删查改权限
grant create,alter,drop,select,insert,update,delete on mybatis_db.* to mybatis@'%'; 

			- 查看用户权限

				- -- 查看用户“mybatis”
				- show grants for mybatis;

		- MySQL 版本查看

			- * 查看MySQL的版本号
			- select version();

- 结构
SQL 语句不区分大小写
但是插入到表中的数据是区分大小写的

	- 数据定义语言（Data Definition Language，DDL）

		- DROP：删除数据库和表等对象
		- CREATE：创建数据库和表等对象
		- ALTER：修改数据库和表等对象的结构

	- 数据操作语言（Data Manipulation Language，DML）

		- INSERT：向表中插入新数据
		- DELETE：删除表中的数据
		- SELECT：查询表中的数据
		- UPDATE：更新表中的数据

	- 数据控制语言（Data Control Language，DCL）

		- GRANT：赋予用户操作权限
		- REVOKE：取消用户的操作权限
		- COMMIT：确认对数据库中的数据进行的变更
		- ROLLBACK：取消对数据库中的数据进行的变更

### pymysql

- 连接

	- db = pymysql.connect(host='127.0.0.1', user='root', password='123456789', database='stationData',charset='utf8')

		- 流数据

			-         db = pymysql.connect(host=host,user=user,password=password,database=database,charset='utf8')
        ssh = db.cursor(cursor=pymysql.cursors.SSCursor)
        ssh.execute("select * from stationA")
        result = ssh.fetchone()
        while result:
            do something
            result = ssh.fetchone()

- 建立通道

	- ssh =db.cursor()

		- ssh移动

			- ssh.scroll(1,mode='absolute')  # 相对绝对位置移动 
			- ssh.scroll(1,mode='relative')  # 相对当前位置移动 

		- 回显数据设置

			- ssh =db.cursor(cursor=pymysql.cursors.DictCursor)

				- 默认是元组型,这里设置为字典型

- 执行指令

	- ssh.execute(cmdStr)

		- 执行一次指令

	- ssh.executemany(cmdStr)

		- 重复执行指令

- 获取回显

	- ssh.fetchone() 获取回显第一行数据 或 ssh所在位置的数据
	- ssh.fetchmany(size:int) 获取回显前size行数据
	- ssh.fetchall() 获取回显的所有数据

- 获取最新数据index

	- index = ssh.lastrowid

- 更新

	- db.commit()

- 回滚

	- db.rollback()

- 断开

	- db.close()

- 总结

	- 1

		- connect() 函数常用参数：

参数	说明
dsn	数据源名称，给出该参数表示数据库依赖
host=None	数据库连接地址
user=None	数据库用户名
password=‘’	数据库用户密码
database=None	要连接的数据库名称
port=3306	端口号，默认为3306
charset=‘’	要连接的数据库的字符编码（可以在终端登陆mysql后使用 \s 查看，如下图）
connect_timeout=10	连接数据库的超时时间，默认为10
port=3306	端口号，默认为3306

	- 2

		- connect() 函数返回的连接对象的方法总结：

方法名	说明
close()	关闭数据库的连接
commit()	提交事务
rollback()	回滚事务
cursor()	获取游标对象，操作数据库，如执行DML操作，调用存储过程等

	- 3

		- 游标对象的方法：

方法名	说明
callproc(procname,[,parameters])	调用存储过程，需要数据库支持
close()	关闭当前游标
execute(operation,[,parameters])	执行数据库操作，sql语句或者数据库命令
executemany(operation, seq_of_params)	用于批量操作
fetchone()	获取查询结果集合中的下一条记录
fetchmany(size)	获取指定数量的记录
fetchall()	获取查询结果集合所有记录
nextset()	跳至下一个可用的数据集
arraysize	指定使用fetchmany()获取的行数，默认为1
setinputsizes(size)	设置调用execute*()方法时分配的内存区域大小
setoutputsizes(size)	设置列缓冲区大小，对大数据列尤其有用

