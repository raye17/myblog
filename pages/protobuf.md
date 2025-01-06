## 标量值类型
	- 标量消息字段可以具有以下类型之一，表格为`.proto`文件中指定的类型以及自动生成的类中的对应类型
	- TODO logseq不支持表格，插入链接 [protobuf语法](https://protobuf.com.cn/programming-guides/proto3/)
- ## 更新protobuf包
  collapsed:: true
	- 更新protobuf包涉及以下几个步骤：
	  collapsed:: true
		- **更新protobuf编译器**：确保使用的是最新版本的protobuf编译器。
		  logseq.order-list-type:: number
		  collapsed:: true
			- 可以从[protobuf的GitHub页面](https://github.com/protocolbuffers/protobuf/releases)下载最新版本。
		- **更新protobuf Go插件**：
		  logseq.order-list-type:: number
		  collapsed:: true
			- `protoc-gen-go`：
			  logseq.order-list-type:: number
			  collapsed:: true
				- ```
				   go get -u github.com/golang/protobuf/protoc-gen-go
				   ```
			- `protoc-gen-go-grpc`：
			  logseq.order-list-type:: number
			  collapsed:: true
				- ```
				   go get -u google.golang.org/grpc/cmd/protoc-gen-go-grpc
				   ```
		- **更新protobuf Go库** 如果使用的是`github.com/golang/protobuf`，使用以下命令更新：
		  logseq.order-list-type:: number
		   ```
		   go get -u github.com/golang/protobuf
		   ```
		   如果需要更新到新的protobuf库`google.golang.org/protobuf`，使用以下命令：
		   ```
		   go get google.golang.org/protobuf
		   ```
		- **更新代码中的导入路径**：
		  logseq.order-list-type:: number
		  collapsed:: true
			- 根据需要更新Go代码中的导入路径，以反映现在使用的库的版本。
			- 例如，如果从`github.com/golang/protobuf`迁移到`google.golang.org/protobuf`，需要将所有的导入路径从`github.com/golang/protobuf/proto`更改为`google.golang.org/protobuf/proto`。
		- **重新生成代码**：
		  logseq.order-list-type:: number
		  collapsed:: true
			- 运行protobuf编译器以重新生成Go代码。运行类似以下命令：
			  logseq.order-list-type:: number
			   ```
			   protoc --go_out=. --go_opt=paths=source_relative --go-grpc_out=. --go-grpc_opt=paths=source_relative path/to/your.proto
			   ```
		- **测试**：确保运行项目的测试套件，验证更新后的protobuf包是否与项目兼容。
		  logseq.order-list-type:: number
		- **注意**，更新protobuf包可能会引入不兼容的更改，因此在进行更新之前，请确保了解这些更改，并在更新后彻底测试项目。
		  logseq.order-list-type:: number