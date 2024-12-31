-
-
-
-
-
- # zookeeper启动命令 #win
  card-last-score:: 5
  card-repeats:: 2
  card-next-schedule:: 2025-01-04T02:28:12.879Z
  card-last-interval:: 4
  card-ease-factor:: 2.7
  card-last-reviewed:: 2024-12-31T02:28:12.880Z
	- ## win
		- ```
		  # 进入 Zookeeper bin 目录
		  cd C:\path\to\zookeeper\bin
		  # 启动客户端 (连接本地Zookeeper)
		  zkCli.cmd
		  
		  # 或者指定地址
		  zkCli.cmd -server 127.0.0.1:2181
		  ```
	- ## docker
		- ```
		  # 进入 Zookeeper 容器
		  docker exec -it zookeeper-container-name bash
		  
		  # 然后运行客户端
		  zkCli.sh
		  ```
	-
- # zookeeper常用命令
	- ```
	  # 列出根节点下的子节点
	  ls /
	  
	  # 列出 dubbo 节点下的子节点
	  ls /dubbo
	  
	  # 获取节点数据
	  get /dubbo/path/to/node
	  
	  # 查看节点详细信息
	  stat /dubbo/path/to/node
	  
	  # 退出客户端
	  quit
	  ```