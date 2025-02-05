- vscode环境配置
	- vscode go 配置
		- 代码检测配置
			- 仅忽略未使用函数警告，保留其他警告
				- 在vscode设置里使用go.lint,配置go.lintFlags
				  logseq.order-list-type:: number
					- ```{
					      "go.lintTool": "golangci-lint",
					      "go.lintFlags": [
					      	"--fast"						跳过一些较慢的 linters，只运行快速的 linters
					          "--disable=unused",				用于禁用 unused linter。
					          "--enable=unused,deadcode",		用于启用 unused 和 deadcode linter。
					          "--exclude-use-default=false",	用于禁用默认的排除规则。
					          "--exclude=U1000"	
					          "--concurrency=4"				并行运行
					      ]
					  }
					  ```
				- 创建.golang.cli.yml文件
				  logseq.order-list-type:: number
					- ```
					  linters-settings:
					    unused:
					      checks:
					        funcs: false
					        vars: true
					  ```
				- 在setting.json文件里更新
				  logseq.order-list-type:: number
					- ```
					  {
					      "go.lintTool": "golangci-lint",
					      "go.lintFlags": [
					          "--fast",
					          "--concurrency=4",
					          "--config=.golangci.yml"  // 使用配置文件
					      ],
					  }
					  ```
		- gopls配置
			- Go 扩展默认是使用大量的 Go 工具来提供各种功能的, 每个工具提供某个方面的能力, 比如代码提示是依靠 gocode 的.
			- 微软在开发 VS Code 过程中, 定义一种协议, 语言服务器协议：[Language Server Protocol](https://link.zhihu.com/?target=https%3A//microsoft.github.io/language-server-protocol/)
			- gopls 就是官方的语言服务器.
			- 安装并设置 gopls
				- 安装方式一
					- 打开 VS Code 的设置, 搜索 `go.useLanguageServe`, 并勾选上. 默认情况下, Go 扩展会提示安装 gopls.
					- 如果长时间安装不上, 可以尝试手动安装: [官方安装指南](https://link.zhihu.com/?target=https%3A//github.com/golang/tools/blob/master/gopls/doc/user.md).
				- 安装方式二
					- 因为网络的问题, 直接去 `https://github.com/golang/tools/tree/master/gopls` 下载, 然后使用 `go install github.com/golang/tools/cmd/gopls` 安装.
				- 安装方式三
					- 网络好, 或者设置 goproxy 代理后, 可以直接手动安装 gopls, 官方提示不要使用 -u.
					- `go get golang.org/x/tools/gopls@latest`
				- 配置
					- 装完之后, 添加如下配置, 如果是第一种安装方式, 第一行已经存在了:
						- ```
						  "go.useLanguageServer": true,
						  "[go]": {
						    "editor.snippetSuggestions": "none",
						    "editor.formatOnSave": true,
						    "editor.codeActionsOnSave": {
						        "source.organizeImports": true
						    }
						  },
						  "gopls": {
						    "usePlaceholders": true, // add parameter placeholders when completing a function
						    "wantCompletionDocumentation": true // for documentation in completion items
						  },
						  "files.eol": "\n", // formatting only supports LF line endings
						  ```
				- 如果需要在不同的编辑器中使用 gopls, 参考官方安装文档中的设置.
			- ​
			-
			-
			-
			-
	-