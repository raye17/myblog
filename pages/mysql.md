-
- ## 表操作
	- ### 创建
		- ```
		  create table table_name(
		  id int primary key,
		  name var，
		  age int
		  )
		  ```
	- ### 查看建表信息
	  collapsed:: true
		- ```
		  describe table_name(describe 可省略成desc)
		  show create table table_name
		  ```
	- ### 修改
		- #### 新增列
			- ```
			  alter table table_name add column email varchar(255);
			  ```
- ### 插入数据
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
- ### SQL语句
	- #### 运算符
		- `<>`：比较运算符，表示不等于。
			- 例：`name <> ''` 为检查name是否为空字符串，不是就为真