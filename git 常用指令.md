# 全局参数

```plain
因为Git是分布式版本控制系统，所以需要填写用户名和邮箱作为一个标识。
git config --global 参数，
有了这个参数，表示这台机器上所有的Git仓库都会使用这个配置，
git config --global user.name "raye"
git config --global user.email "raye@example.com"
git config --global user.password "password"
也可以对某个仓库指定的不同的用户名和邮箱，进入制定仓库，去掉global即可
修改user.name
<1>git bash(替换)
git config --global --replace-all user.name "your user name"
<2> 修改 .gitconfig文件
<3>git config -e 
自己选择删除
<4>覆盖
git config --global user.name "example"
删除对应的用户名或邮箱
git config --global --unset-all user.name（user.email）
```
# 版本回退

```plain
#查看日志
git log 
#简洁日志
git log --pretty=oneline
#查看所有版本号
git reflog
#版本回退
<1>git reset --hard HEAD^^^(一个^代表一个版本)
<2>git reset --hard HEAD~199
<3>git reset --hard 版本号
#撤销修改
git checkout --<file>撤销工作区的更改

```
# 远程仓库remote

## 创建ssh key

```plain
ssh-keygen -t rsa -C "email@example.com"
一直回车默认or修改sshkey文件位置
```

## 分支branch

```plain
#创建分支
git checkout dev
#创建并切换分支
git checkout -b dev
#创建远程分支到本地
git checkout -b dev origin/dev
#指定本地dev分支与远程origin/dev分支的链接
git branch --set-upstream dev origin/dev
#合并分支
git merge(合并指定分支到当前分支)
#删除分支
git branch -d name
#bug分支(创建临时分支)
git stash（把当前工作区隐藏）
git checkout master（切换到主分支）
git checkout -b 临时分支
<编辑>
切换到主分支，合并并删除临时分支
再回到之前的分支
git stash list(查看)
<1>git stash apply 恢复后，stash内容并不删除，使用命令git stash drop来删除
<2>git stash pop 恢复的同时把stash内容也删除
```

# pull/push

```plain
git push <远程主机名> <本地分支>:<远程分支>
省略本地分支等价于删除远程分支（git push origin :dev）
#删除远程仓库的分支
git push origin --delete dev
同步远程仓库
git pull <远程主机名> <远程分支>:<本地分支>
git pull origin master :my_test 
如果省略本地分支，则将自动合并到当前所在分支上
git pull origin master
```

#### 
# commit

```plain
#将暂存区改动提交到本地版本库
git commit -m "edit"
#撤回commit
git reset --soft HEAD^(如果控制台出现More?，则将命令改成 git reset --soft HEAD^^即可)
仅是撤回commit操作，写的代码仍然保留
#参数
–mixed
不删除工作空间改动代码，撤销commit，并且撤销git add . 操作
这个为默认参数,git reset --mixed HEAD^ 和 git reset HEAD^ 效果是一样的。
–soft
不删除工作空间改动代码，撤销commit，不撤销git add .
–hard
删除工作空间改动代码，撤销commit，撤销git add .
注意完成这个操作后，就恢复到了上一次的commit状态。
#修改注释 
如果commit注释写错了，只是想改一下注释，只需要：
git commit --amend

```

# 

# git 常见问题

1. 使用http/https协议每次pull或者push需要输入密码
```plain
git config --global credential.helper store
会在本地生成.gitconfig
执行命令：
cat ~/.gitconfig，
存在如下内容即代表成功
[credential]
helper = store
再输入一次后，无需再输入
```
2. 公司为了安全，3个月强制改密码，此时执行也会出问题
```plain
remote: HTTP Basic: Access denied
fatal: Authentication failed for 'http://git.aaa.com/aaa/aaa.git/'
解决方法：密码重置
git config --system --unset credential.helper
```
3. goland终端配置git bash
[参考](https://blog.csdn.net/liu865033503/article/details/103630499?ops_request_misc=&request_id=&biz_id=102&utm_term=win%20%20git%20%E6%B2%A1%E6%9C%89ll%20&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-103630499.142^v72^insert_down3,201^v4^add_ask&spm=1018.2226.3001.4187)

4. 

