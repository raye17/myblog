# 下载go环境
	- 下载go安装包： [go下载链接](https://golang.google.cn/dl/)
	- ![](https://i-blog.csdnimg.cn/blog_migrate/f3ef4e55cb1f43e128f590239b04fd3a.png)
- # 解压到指定目录，如GOROOT
- # 配置环境变量，设置GOROOT，GOPATH
- # 配置 GO111MODULE、GOPROXY、GOSUMDB
	- ```
	  Go默认的GOPROXY的值是：GOPROXY=https://proxy.golang.org,direct。
	  这个goproxy在使用go get安装第三方库的时候会报错，导致无法下载成功，所以要修改一下。
	  改为：https://goproxy.io,direct （七牛镜像）或 https://mirrors.aliyun.com/goproxy（阿里云镜像）
	  ```
- ```
  #开启mod模式（项目管理需要用到）
  go env -w GO111MODULE=on
  #重新设置成七牛镜像源（推荐）或阿里镜像源（用原有的会比较慢）
  go env -w GOPROXY=https://goproxy.cn,direct
  go env -w GOPROXY=https://mirrors.aliyun.com/goproxy
  win失败可以用set GOPROXY=https://goproxy.cn,direct
  #关闭包的MD5校验
  go env -w GOSUMDB=off
  
  #查看环境变量
  go env
  
  ```