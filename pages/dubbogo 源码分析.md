- ```
  dubbo启动：
  dubbo会调用dubbo.apache.org/dubbo-go/v3/config 下的config.Load()获取yaml配置文件
  在不传参的情况下，load会调用NewLoaderConf() 
  newLoaderConf()返回文件路径为../conf/dubbogo.yaml
  ```