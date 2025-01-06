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
	- ###
	- ## 解决viper读取yaml配置存在下划线时无法映射
		-
		- ### 适用场景：使用viper读取yaml文件时候，遇到yaml文件中存在下划线，映射到结构体之后，结构体无法取到yaml文件中对应的值。
		- conf.yaml文件如下：
		- mysql:
		  rds_host: "rds_xxxxxx.com"
		  rds_port: 3306
		  1
		  2
		  3
		  config.go部分内容如下：
		- type Mysql struct {
		  RdsHost string `yaml:"rds_host" mapstructure:"rds_host"`
		  RdsPort int    `yaml:"rds_port" mapstructure:"rds_port"`
		  }
		- type Config struct {
		  Mysql  Mysql  `yaml:"mysql"`
		  }
		- var Conf *Config
		- func InitConf(confPath string) {
		  var err error
		    
		  v := viper.New()
		  v.SetConfigName("config")
		  v.SetConfigType("yaml")
		  v.AddConfigPath("xxxxxx")
		- err = v.ReadInConfig()
		  if err != nil {
		  logrus.Errorf("[viper] ReadInConfig err:%s", err.Error())
		  return
		  }
		- err = v.Unmarshal(&Conf)
		  if err != nil {
		  logrus.Errorf("[viper] Unmarshal err:%s", err.Error())
		  panic(err)
		  }
		    
		    // 省略...
		  return
		  }
		  1
		  2
		  3
		  4
		  5
		  6
		  7
		  8
		  9
		  10
		  11
		  12
		  13
		  14
		  15
		  16
		  17
		  18
		  19
		  20
		  21
		  22
		  23
		  24
		  25
		  26
		  27
		  28
		  29
		  30
		  31
		  32
		  33
		  34
		  在读取yaml映射到Conf结构体时，发现Mysql中的RdsHost和RdsPort都是空值，仔细检查，发现tag中的
		- 字段也是对得上的，为何不映射不到？
		- 翻了翻viper解析的部分源码，发现有些特殊情况，需要自定义kv的分隔符，有些时候，需要添加一些特殊标记来告诉解析器，这是一个合法的标识符。
		- 将Mysql的结构体添加mapstructure，指定对应的字段就行了：
		- type Mysql struct {
		  RdsHost string `yaml:"rds_host" mapstructure:"rds_host"`
		  RdsPort int    `yaml:"rds_port" mapstructure:"rds_port"`
		  ————————————————
		- 版权声明：本文为博主原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接和本声明。
		                        
		  原文链接：https://blog.csdn.net/weixin_42677653/article/details/123974540