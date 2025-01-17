## 库操作
	- ```
	  基本操作：
	  # 创建数据库
	  CREATE DATABASE myDatabase;
	  # 查看数据库
	  	查看所有数据库：
	  		SHOW DATABASES;
	  	查看某个数据库的详细信息：
	  		SHOW CREATE DATABASE myDatabase;
	  # 删除数据库
	  DROP DATABASE myDatabase;
	  # 切换数据库
	  USE myDatabase;
	  在执行这些操作之前，确保有足够的权限，并且在进行删除操作之前，确保已经备份重要数据，以防不慎删除。
	  ```
- ## 表操作
	- ###  表级
	  collapsed:: true
		- ### 创建
			- ```
			  create table table_name(
			  id int primary key,
			  name var，
			  age int
			  )
			  ```
		- ### 查看建表信息
			- ```
			  查看所有表：
			  show tables
			  查看某个表：
			  describe table_name(describe 可省略成desc)
			  show create table table_name
			  ```
	- ### 列级
		- #### 新增
			- ```
			  alter table table_name add column email varchar(255);
			  ```
		- #### 删除
		  collapsed:: true
			- ```
			  ALTER TABLE table_name DROP COLUMN columnName;
			  ```
		- #### 重命名
			- ```
			  -- 使用 CHANGE 关键字
			  ALTER TABLE table_name CHANGE oldColumnName newColumnName columnType;
			  
			  -- 使用 RENAME 关键字
			  ALTER TABLE table_name RENAME COLUMN oldColumnName TO newColumnName;
			  
			  ```
		- #### 修改数据类型
			- ```
			  ALTER TABLE table_name MODIFY COLUMN columnName newColumnType;
			  ```
- ## 数据操作
	- ### 查询
		- **多表查询**
			- 内连接
			  logseq.order-list-type:: number
			- 外连接
			  logseq.order-list-type:: number
		- ```
		  ```
	- ### 插入
		- ```
		   # 单行插入
		   	## 插入全列数据
		   		INSERT INTO table_name (id, name，age) VALUES (1, 'Alice',17);
		          简写 insert into table_name vaues(1,'Alice',17)(表结构发生变化时会出错)
		      ## 插入指定列
		      	insert into table_name (id,name) values (1,'Alice')
		   ## 批量插入
		   		insert into table_name (id,name) values
		          (1,'Alice'),
		          (2,'Bob'),
		          (3,'raye');
		  ```
	- ### 更新
		- ```
		  单行更新
		  -- 更新 id 为 1 的行的 email 列
		  UPDATE table_name SET email = 'alice@example.com' WHERE id = 1;
		  
		  -- 更新 id 为 2 的行的 email 列
		  UPDATE table_name SET email = 'bob@example.com' WHERE id = 2;
		  
		  -- 更新 id 为 3 的行的 email 列
		  UPDATE table_name SET email = 'charlie@example.com' WHERE id = 3;
		  
		  批量更新
		  UPDATE table_name SET email = CASE id
		      WHEN 1 THEN 'alice@example.com'
		      WHEN 2 THEN 'bob@example.com'
		      WHEN 3 THEN 'charlie@example.com'
		      ELSE email  
		  END;
		  
		  ```
- ### SQL语句
	- #### 运算符
		- `<>`：比较运算符，表示不等于。
			- 例：`name <> ''` 为检查name是否为空字符串，不是就为真