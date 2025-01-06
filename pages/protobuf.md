## 标量值类型
	- 标量消息字段可以具有以下类型之一，表格为`.proto`文件中指定的类型以及自动生成的类中的对应类型
	- TODO logseq不支持表格，插入链接 [protobuf语法](https://protobuf.com.cn/programming-guides/proto3/)
- ## 更新protobuf包
	- 更新protobuf包涉及以下几个步骤：
	  collapsed:: true
		- **更新protobuf编译器**：确保使用的是最新版本的protobuf编译器。可以从[protobuf的GitHub页面](https://github.com/protocolbuffers/protobuf/releases)下载最新版本。
		  logseq.order-list-type:: number
		- **更新protobuf Go插件**：
		  logseq.order-list-type:: number
			- `protoc-gen-go`：
			- ```sh
			   go get -u github.com/golang/protobuf/protoc-gen-go
			   ```
			  
			  `protoc-gen-go-grpc`：
			   ```sh
			   go get -u google.golang.org/grpc/cmd/protoc-gen-go-grpc
			   ```
		- **更新protobuf Go库**：更新您的项目中使用的protobuf Go库。如果您使用的是`github.com/golang/protobuf`，可以使用以下命令更新：
		  logseq.order-list-type:: number
		   ```sh
		   go get -u github.com/golang/protobuf
		   ```
		   如果您需要更新到新的protobuf库`google.golang.org/protobuf`，可以使用以下命令：
		   ```sh
		   go get google.golang.org/protobuf
		   ```
		- logseq.order-list-type:: number
		  4. **更新代码中的导入路径**：根据需要更新您的Go代码中的导入路径，以反映您现在使用的库的版本。例如，如果您从`github.com/golang/protobuf`迁移到`google.golang.org/protobuf`，您需要将所有的导入路径从`github.com/golang/protobuf/proto`更改为`google.golang.org/protobuf/proto`。
		- logseq.order-list-type:: number
		  5. **重新生成代码**：运行protobuf编译器以重新生成您的Go代码。这通常涉及到运行类似以下命令：
		   ```sh
		   protoc --go_out=. --go_opt=paths=source_relative --go-grpc_out=. --go-grpc_opt=paths=source_relative path/to/your.proto
		   ```
		- logseq.order-list-type:: number
		  6. **测试**：确保运行项目的测试套件，验证更新后的protobuf包是否与您的项目兼容。
		- 请注意，更新protobuf包可能会引入不兼容的更改，因此在进行更新之前，请确保您了解这些更改，并在更新后彻底测试您的项目。
		  logseq.order-list-type:: number