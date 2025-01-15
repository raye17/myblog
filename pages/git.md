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