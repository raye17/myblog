-
- ## 表操作
	- ### 创建
		- ```
		  create table table_name(
		  id int primary key,
		  name var
		  )
		  ```
	- ### 查看建表信息
		- ```
		  describe table_name(describe 可省略成desc)
		  show create table table_name
		  ```
	- ### 插入数据
		- 单行插入
		  logseq.order-list-type:: number
			- ```
			   INSERT INTO table_name (id, name) VALUES (1, 'Alice');
			  ```
		- 批量插入
		  logseq.order-list-type:: number
- ### SQL语句
	- #### 运算符
		- `<>`：比较运算符，表示不等于。
			- 例：`name <> ''` 为检查name是否为空字符串，不是就为真