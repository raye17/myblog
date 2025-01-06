## 读取路径
	- ```
	  viper.SetConfigName("personal_info")  // 配置文件名 (不需要扩展名)
	  viper.SetConfigType("yaml")           // 如果是 YAML 格式
	  viper.AddConfigPath("doc")            // 配置文件所在的路径
	  ```
-
-
-
-
-
-
- # Question
	-
	- ## 解决viper读取yaml配置存在下划线时无法映射
		- ### 场景：
			- 使用viper读取yaml文件时候，遇到yaml文件中存在下划线，映射到结构体之后，结构体无法取到yaml文件中对应的值。
			- yaml文件如下：
			- ```
			  	experience: 
			      - company: Example Inc.
			        position: Software Engineer
			        start_year: 2013 
			        end_year: 2019 
			  ```
			- model文件如下：
			- ```
			  	type Person struct {
			  	Name    string `yaml:"name"`
			  	......
			  	Experience []struct {
			  		Company   string `yaml:"company"`
			  		Position  string `yaml:"position"`
			  		StartYear int    `yaml:"start_year"`
			  		EndYear   int    `yaml:"end_year"`
			  	} `yaml:"experience"`
			  	......
			  }
			  ```
			- 在读取yaml映射到Conf结构体时，发现Mysql中的RdsHost和RdsPort都是空值，仔细检查，发现tag中的
			- 字段也是对得上的，为何不映射不到？
			- 翻了翻viper解析的部分源码，发现有些特殊情况，需要自定义kv的分隔符，有些时候，需要添加一些特殊标记来告诉解析器，这是一个合法的标识符。
		- 将Mysql的结构体添加mapstructure，指定对应的字段就行了：
		- type Mysql struct {
		  RdsHost string `yaml:"rds_host" mapstructure:"rds_host"`
		  RdsPort int    `yaml:"rds_port" mapstructure:"rds_port"`
		  ————————————————
		- 版权声明：本文为博主原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接和本声明。
		                        
		  原文链接：https://blog.csdn.net/weixin_42677653/article/details/123974540