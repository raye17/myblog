### git add
	- git add 添加多个文件，文件中间用空格隔开
	  logseq.order-list-type:: number
		- `git add file1 file2`
		  logseq.order-list-type:: number
	- 多次git add
	  logseq.order-list-type:: number
		- logseq.order-list-type:: number
		  ```
		  git add file1
		  git add file2
		  git add file3
		  ```
	- 添加指定目录下的文件
	  logseq.order-list-type:: number
		- logseq.order-list-type:: number
		  ```
		  # config目录下及子目录下所有文件，home目录下的所有.php文件
		  git add config/*
		  git add home/*.php
		  ```
	- git add文件夹名
	  logseq.order-list-type:: number
-
- ## subModule
	- ### 为什么要subModule
		- **解决公共代码问题**。如果某些文件，在项目A和项目B中都会用到，例如组件库，那么这些文件可以作为 submodules 来管理，减少重复代码。（npm包是另一解决方案）
		- **解决团队维护难题**。如果一个大项目是一个大 Git 仓库，需要统一编译，不同的模块由不同团队维护，放在同一个 Git 仓库有诸多难处：例如多个团队的 MR 混在一起、权限难以区分等。这种情况即使公司内网 Git 权限做的足够精细，仓库管理员的学习成本也会很高，很难深度使用这种高级功能。为了解决多团队维护的难题，Git Submodules 也能大展身手，它可以让每个团队负责的模块就是一个 Git 仓库，这些 Git 仓库都被包含在同一个主 Git 项目下。（微前端、微服务是另一种解决方案。）
	- ### 了解SubModule
		- 一个仓库做另一个仓库的子模块，两者都是完整的git仓库
	- ### 创建SubModule
		- ```
		  git init ProjectA
		  git init ProjectB
		  在A仓库下 
		  git submodule add (projectB地址；即git clone 后面的地址)
		  ```
		- **注意事项**
			- 执行操作后，会在当前父项目下新建个文件夹，名字就是 submodule 仓库的名字。文件夹里面的内容，**是 submodule 对应 Git 仓库的完整代码。**
			- 如果希望换个名字，或者换个路径（例如放在某个更深的目录下），也是允许的，需要后面增加个路径参数，例如`git submodule add ...(仓库地址) src/B(希望 submodule 位于的文件夹路径)`
		- **submodule 的父子关系存在哪里**
			- 关系是保存在主项目的 Git 仓库中。
			- 被当作 submodule 的 Git 仓库，其实不知道自己变成了 submodule，它更不知道爸爸们有谁。（意思是，当打开某个被当作 submodule 的 Git 仓库首页时，或者拉下这个仓库时，没有任何痕迹表明它是个submodule。因为父子信息不存在这里，只存在爸爸那里。）
		- ### SubModule信息保存
			- 存在于主项目的`.gitmodule`文件里
			- 主项目还保存了对应 submodule 的版本号（commit id），没有冗余存储 submodule 的代码。
- ## 仓库
	-
- ## 分支
	- ### 新建分支
	  collapsed:: true
		- ```
		  #第一步，切换到指定的分支。如从dev上拉一个分支
		  git checkout dev 
		  #第二步，拉取dev的最新代码
		  git pull
		  #第三步，在本地创建一个test分支，并切换到该分支。此时执行git branch会看到该分支在本地已创建
		  git checkout -b test 
		  #第四步，把分支推到远程仓库。此时执行git branch -av可以看到该分支在远程仓库也有了
		  git push origin test
		  #第五步，将本地分支与远程分支关联
		  git branch --set-upstream-to=origin/test test
		  ```
			-
	- ### 删除分支
		- ```
		  删除远程分支：
		  git push origin --delete <branch-name>
		  删除本地分支：
		  git branch -d <branch-name>
		  如果该分支没有被完全合并，可以使用强制删除：
		  git branch -D <branch-name>
		  ```