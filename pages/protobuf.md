## 标量值类型
	- 标量消息字段可以具有以下类型之一，表格为`.proto`文件中指定的类型以及自动生成的类中的对应类型
	- TODO logseq不支持表格，插入链接 [protobuf语法](https://protobuf.com.cn/programming-guides/proto3/)
- ## 更新protobuf包
	- 更新protobuf包通常涉及以下几个步骤：
	- **更新protobuf编译器**：确保您使用的是最新版本的protobuf编译器。您可以从[protobuf的GitHub页面](https://github.com/protocolbuffers/protobuf/releases)下载最新版本。
	  logseq.order-list-type:: number
	- 2. **更新protobuf Go插件**：如果您使用的是`protoc-gen-go`插件，您可以通过以下命令更新到最新版本：
	   ```sh
	   go get -u github.com/golang/protobuf/protoc-gen-go
	   ```
	   对于`protoc-gen-go-grpc`插件，使用以下命令更新：
	   ```sh
	   go get -u google.golang.org/grpc/cmd/protoc-gen-go-grpc
	   ```
	- 3. **更新protobuf Go库**：更新您的项目中使用的protobuf Go库。如果您使用的是`github.com/golang/protobuf`，可以使用以下命令更新：
	   ```sh
	   go get -u github.com/golang/protobuf
	   ```
	   如果您需要更新到新的protobuf库`google.golang.org/protobuf`，可以使用以下命令：
	   ```sh
	   go get google.golang.org/protobuf
	   ```
	- 4. **更新代码中的导入路径**：根据需要更新您的Go代码中的导入路径，以反映您现在使用的库的版本。例如，如果您从`github.com/golang/protobuf`迁移到`google.golang.org/protobuf`，您需要将所有的导入路径从`github.com/golang/protobuf/proto`更改为`google.golang.org/protobuf/proto`。
	- 5. **重新生成代码**：运行protobuf编译器以重新生成您的Go代码。这通常涉及到运行类似以下命令：
	   ```sh
	   protoc --go_out=. --go_opt=paths=source_relative --go-grpc_out=. --go-grpc_opt=paths=source_relative path/to/your.proto
	   ```
	- 6. **测试**：确保运行项目的测试套件，验证更新后的protobuf包是否与您的项目兼容。
	- 请注意，更新protobuf包可能会引入不兼容的更改，因此在进行更新之前，请确保您了解这些更改，并在更新后彻底测试您的项目。