## 读取路径
	- ```
	  viper.SetConfigName("personal_info")  // 配置文件名 (不需要扩展名)
	  viper.SetConfigType("yaml")           // 如果是 YAML 格式
	  viper.AddConfigPath("doc")            // 配置文件所在的路径
	  ```
-