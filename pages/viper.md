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
			- 在读取`yaml`映射到`model`结构体时，`Person`中的`StartYear`和`EndYear`都是空值，检查发现`tag`中的字段也对得上的，但却映射不到
			- 根据`viper`解析的部分[源码](https://github.com/spf13/viper/blob/master/viper.go)，发现有些特殊情况，需要自定义kv的分隔符，有些时候，需要添加一些特殊标记来告诉解析器，这是一个合法的标识符。
			- 将`Person`的结构体添加`mapstructure`，指定对应的字段就行了：
			- ```
			  Experience []struct {
			  		Company   string `yaml:"company"`
			  		Position  string `yaml:"position"`
			  		StartYear int    `yaml:"start_year" mapstructure:"start_year"`
			  		EndYear   int    `yaml:"end_year" mapstructure:"end_year"`
			  	} `yaml:"experience"`
			  ```
		-