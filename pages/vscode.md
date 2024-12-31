- vscode环境配置
	- vscode go代码检测配置#vscode #go
		- 仅忽略未使用函数警告，保留其他警告
			- 在vscode设置里使用go.lint,配置go.lintFlags
			  logseq.order-list-type:: number
			  collapsed:: true
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
			  collapsed:: true
				- ```
				  linters-settings:
				    unused:
				      checks:
				        funcs: false
				        vars: true
				  ```
			- 在setting.json文件里更新
			  logseq.order-list-type:: number
			  collapsed:: true
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
	- go配置 [[2024-12-24]]