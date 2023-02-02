# 目录

## mkdir

```plain
mkdir //创建目录
mkdir test 
mkdir -p //创建目录/子目录；允许创建目录及子目录；也可以在绝对路径下创建目录
mkdir -p /home/test
mkdir -m //再已存在目录或路径下创建指定权限的目录
mkdir -m 777 /home/test
mkdir –v//创建完成后提示完成
mkdir -v test
mkdir test01 test02 test03 //在当前目录创建多个目录
mkdir -vp test/test01 //创建test的基础上创建test01，并提示
mkdir -p -m 755 /home/test/tets01
//在绝对路径下的目录中去创建目录
//然后给这个空目录权限值中的权限
//这个绝对路径下的目录可存在也可不存在
```


## tree

```plain
-a  打印所有文件,包括隐藏文件、目录
-C  在文件和目录清单上加上色彩，便于区分文件类型
-d  仅列出目录名称，而非内容
-D  列出文件或目录更改时间
-f  打印每个文件的完整路径前缀
-F  在每个条目后加上文件类型的指示符(如目录是/)
-l  跟随目录的符号链接，就像它们是目录一样。 避免了导致递归循环的链接
-L  目录树的最大显示深度
-p  打印结构同时打印文件权限
```
## 权限

权限包括读（r）,写（w）,执行(execute)（x）

### 更改权限（chmod）

[权限详解参考](https://blog.csdn.net/u013197629/article/details/73608613?ops_request_misc=&request_id=&biz_id=102&utm_term=linux%E6%9D%83%E9%99%90&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-73608613.142^v63^control,201^v3^control_1,213^v2^t3_esquery_v2&spm=1018.2226.3001.4187)

## grep 命令

```
grep -i "test" test.txt 搜索时不区分大小写
grep -n "test" test.txt 显示所在行号
grep --color 高亮
grep -c "test" test.txt 统计符合条件行数
grep -o 关键字
grep -B <n> 前n行
grep -A <n> 后n行
grep -C <n> 前后n行
grep -w 精确搜索
grep -v  "tets" 不查找该字符
grep -e "test" -e"abc" 多关键词查找
```

