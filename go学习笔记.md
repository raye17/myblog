# 学习帮助

1. [go学习指导](https://blog.csdn.net/qq_34896199/article/details/107204994?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166778570216800184159021%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166778570216800184159021&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~times_rank-13-107204994-null-null.142^v63^control,201^v3^control_1,213^v1^control&utm_term=%E6%96%B0%E6%89%8Bgo%E8%AF%AD%E8%A8%80%E6%8E%A8%E8%8D%90%E4%B9%A6&spm=1018.2226.3001.4187)
2. [go语言圣经网站](https://books.studygolang.com/gopl-zh/ch1/ch1-01.html)
3. [go语言笔记](https://mp.weixin.qq.com/s/OYhZ4XANbaFH4f9g4EZ-Ig)


# 学习记录
# go 基础

## 数据类型

### 整型

整型分为以下两个大类：

按长度分为：int8、int16、int32、int64 

对应的无符号整型：uint8、uint16、uint32、uint64

其中，`uint8`就是我们熟知的 `byte`型，`int16`对应 C 语言中的 `short`型，`int64`对应 C 语言中的 `long`型。 

| 类型     | 描述                                                      |
|:-------|:--------------------------------------------------------|
| uint8  | 无符号 8 位整型 (0 到 255)                                     |
| uint16 | 无符号 16 位整型 (0 到 65535)                                  |
| uint32 | 无符号 32 位整型 (0 到 4294967295)                             |
| uint64 | 无符号 64 位整型 (0 到 18446744073709551615)                   |
| int8   | 有符号 8 位整型 (-128 到 127)                                  |
| int16  | 有符号 16 位整型 (-32768 到 32767)                             |
| int32  | 有符号 32 位整型 (-2147483648 到 2147483647)                   |
| int64  | 有符号 64 位整型 (-9223372036854775808 到 9223372036854775807) |

特殊整型

| 类型      | 描述                                    |
|:--------|:--------------------------------------|
| uint    | 32 位操作系统上就是 uint32，64 位操作系统上就是 uint64 |
| int     | 32 位操作系统上就是 int32，64 位操作系统上就是 int64   |
| uintptr | 无符号整型，用于存放一个指针                        |

**注意：**在使用 `int`和 `uint`类型时，不能假定它是 32 位或 64 位的整型，而是考虑 `int`和 `uint`可能在不同平台上的差异。

**注意事项：**获取对象的长度的内建 `len()`函数返回的长度可以根据不同平台的字节长度进行变化。实际使用中，切片或 map 的元素数量等都可以用 `int`来表示。在涉及到二进制传输、读写文件的结构描述时，为了保持文件的结构不会受到不同编译目标平台字节长度的影响，不要使用 `int`和 `uint`。 

### 进制

## 数字字面量语法（Number literals syntax）
Go1.13 版本之后引入了数字字面量语法，这样便于开发者以二进制、八进制或十六进制浮点数的格式定义数字，例如：

| 进制   | 格式         | 对应进制        | 对应十进制 | 格式化输出 |
|:-----|:-----------|:------------|:------|:------|
| 二进制  | 0b00101101 | 101101(2)   | 45    | %b    |
| 八进制  | 0o377      | 377(8)      | 255   | %o    |
| 十六进制 | 0x1p-2     | 1/(2^2)(16) | 0.25  | %x    |

`v := 0b00101101`， 代表二进制的 101101，相当于十进制的 45。

`v := 0o377`，代表八进制的 377，相当于十进制的 255。

`v := 0x1p-2`，代表十六进制的 1 除以 2²，也就是 0.25。

而且还允许用`_`来分隔数字，比如说：`v := 123_456`表示 v 的值等于 123456。 

### 浮点型

Go 语言支持两种浮点型数：`float32`和 `float64`。

这两种浮点型数据格式遵循 `IEEE 754`标准：

`float32`的浮点数的最大范围约为`3.4e38`，可以使用常量定义：`math.MaxFloat32`。`float64`的浮点数的最大范围约为`1.8e308`，可以使用一个常量定义：`math.MaxFloat64`。

打印浮点数时，可以使用 `fmt`包配合动词`%f` 

| 浮点型数    | 最大范围    | 常量定义            | 遵循标准     |
|:--------|:--------|:----------------|:---------|
| float32 | 3.4e38  | math.MaxFloat32 | IEEE 754 |
| float64 | 1.8e308 | math.MaxFloat64 | IEEE 754 |

```
package main
import (
        "fmt"
        "math"
)
func main() {
        fmt.Printf("%f\n", math.Pi)
        fmt.Printf("%.2f\n", math.Pi)
}
```
### 复数

complex64 和 complex128

```
var c1 complex64
c1 = 1 + 2i
var c2 complex128
c2 = 2 + 3i
fmt.Println(c1)
fmt.Println(c2)

复数有实部和虚部，complex64 的实部和虚部为 32 位，complex128 的实部和虚部为 64 位。
```
### 布尔（bool）

Go 语言中以 `bool`类型进行声明布尔型数据，布尔型数据只有 `true（真）`和 `false（假）`两个值。

**注意：**

1. 布尔类型变量的默认值为 `false`。
2. Go 语言中不允许将整型强制转换为布尔型.
3. 布尔型无法参与数值运算，也无法与其他类型进行转换。
### [字符串](https://so.csdn.net/so/search?q=%E5%AD%97%E7%AC%A6%E4%B8%B2&spm=1001.2101.3001.7020)

Go 语言中的字符串以原生数据类型出现，使用字符串就像使用其他原生数据类型（int、bool、float32、float64 等）一样。

Go 语言里的字符串的内部实现使用 `UTF-8`编码。字符串的值为`双引号(")`中的内容，可以在 Go 语言的源码中直接添加非 ASCII 码字符 。

#### 字符串转义符

| 转义符 | 含义                |
|:----|:------------------|
| \r  | 回车符（返回行首）         |
| \n  | 换行符（直接跳到下一行的同列位置） |
| \t  | 制表符               |
| \'  | 单引号               |
| \"  | 双引号               |
| \\  | 反斜杠               |

```
package main
import (
    "fmt"
)
func main() {
    fmt.Println("str := \"c:\\Code\\lesson1\\go.exe\"")
}
```
#### 多行字符串

```
Go 语言中要定义一个多行字符串时，就必须使用反引号字符：
s1 := `第一行
第二行
第三行
`
fmt.Println(s1)
```
ps:反引号间换行将被作为字符串中的换行，但是所有的转义字符均无效，文本将会原样输出。
#### 字符串常用操作：

| 方法                                  | 介绍      |
|:------------------------------------|:--------|
| len(str)                            | 求长度     |
| +或 fmt.Sprintf                      | 拼接字符串   |
| strings.Split                       | 分割      |
| strings.Contains                    | 判断是否包含  |
| strings.HasPrefix,strings.HasSuffix | 前缀/后缀判断 |
| strings.Index(),strings.LastIndex() | 子串出现的位置 |
| strings.Join(a[]string, sep string) | join 操作 |

### byte 和 rune

[详解](http://www.ruanyifeng.com/blog/2007/10/ascii_unicode_and_utf-8.html)

组成每个字符串的元素叫做“字符”，可以通过遍历或者单个获取字符串元素获得字符。 字符用单引号（’）包裹起来。

Go 语言的字符有以下两种：

1. `uint8`类型，或者叫 byte 型，代表一个 `ASCII 码`字符。
2. `rune`类型，代表一个`UTF-8 字符`。
 当需要处理中文、日文或者其他复合字符时，则需要用到 `rune`类型。`rune`类型实际是一个 `int32`。

字符串底层是一个 byte 数组，所以可以和`[]byte`类型相互转换。字符串是不能修改的。字符串是由 byte 字节组成，所以字符串的长度是 byte 字节的长度。rune 类型用来表示 utf8 字符，一个 rune 字符由一个或多个 byte 组成。 

#### 修改字符串

要修改字符串，需要先将其转换成`[]rune`或`[]byte`，完成后再转换为`string`。无论哪种转换，都会重新分配内存，并复制字节数组。 

```plain
func changeString() {
	s1 := "big"
	// 强制类型转换
	byteS1 := []byte(s1)
	byteS1[0] = 'p'
	fmt.Println(string(byteS1))

	s2 := "白萝卜"
	runeS2 := []rune(s2)
	runeS2[0] = '红'
	fmt.Println(string(runeS2))
}
```
### map

```
#判断map中键是否存在的特殊写法，格式如下:
value, ok := map[key]
如果key存在ok为true,value为对应的值；不存在ok为false,value为值类型的零值
```
### 结构体

#### tag

```
type student struct{
Name string `json:"name"`
}
使用 tag 可以让结构体内数据在返回 json 时以小写出现
```

### 
### 通道(channel)

```
#初始化
##无缓冲通道
chan01:=make(chan string)
##有缓冲通道
make(chan int,3)（容量为3）
#单向通道
<-chan string 只接受，不发送
chan <- int 只发送，不接受
```
## 遍历

### 字符串遍历

go中有两种方式对[字符串](https://so.csdn.net/so/search?q=%E5%AD%97%E7%AC%A6%E4%B8%B2&spm=1001.2101.3001.7020)进行遍历，一种是utf-8遍历，另一种是Unicode遍历

```
package main

import "fmt"

func main() {
str := "Hello,世界"
//utf-8遍历
for i := 0; i < len(str); i++ {
 ch := str[i]
 fmt.Println(ch)
}
fmt.Println("=============>Unicode遍历")
//Unicode遍历
for _, ch1 := range str {
 fmt.Println(ch1)
}
}
```
## 包

包介绍：

Go语言中支持模块化的开发理念，在Go语言中使用`包（package）`来支持代码模块化和代码复用。一个包是由一个或多个Go源码文件（.go结尾的文件）组成，是一种高级的代码复用方案，Go语言为我们提供了很多内置包，如`fmt`、`os`、`io`等。 

定义包：

我们可以根据自己的需要创建自定义包。一个包可以简单理解为一个存放`.go`文件的文件夹。该文件夹下面的所有`.go`文件都要在非注释的第一行添加如下声明，声明该文件归属的包。 

```
package packageName
其中：
package：声明包的关键字
packagename：包名，不能包含 - 符号，最好与其实现的功能相对应。
一个文件夹下面直接包含的文件只能归属一个包，同一个包的文件不能在多个文件夹下。
main包是应用程序的入口包，这种包编译后会得到一个可执行文件，而编译不包含main包的源代码则不会得到可执行文件。
```
## 标准库

### fmt

#### scan,scanf,scanln

```
scanf：
按照给定的格式依次读取数据（包括非法数据），不能换行输入;
如果要换行需要在前面加一个scanln吸收掉回车符，就像c语言中的getchar
scan：
比scanf高级，依次读取数据，遇到回车会忽略，可以换行输入;
如果要先用了scan输入，再用scanf输入的话，需要在中间加一个scanln
scanln：
类似scan，但是遇到换行（回车）立马结束输入，如果要换行输入必须用多个scanln
```
问题描述
在for循环中输入一个字符

```
var choice byte
fmt.Scanf("%c",&choice)
在第二次循环时，该输入语句会被直接跳过

进行测试后发现
0
unexpected newline

判断是将换行符当作字符读取了
可能是由于在缓冲区中仍存在上一次输入留下的换行符（\n）
可以在语句中加上换行符
fmt.Scanf("%c \n",&choice)
```

### 
### io

### [io包](https://github.com/raye17/go/blob/test/study/package/io)
time

#### 基础使用

```
//获取秒级时间戳
time.Now().Unix()
//获取毫秒级时间戳
time.Now().UnixNano()/1e6
// 纳秒级时间戳
fmt.Println(now.UnixNano())
// 时间戳小数部分 单位：纳秒
fmt.Println(now.Nanosecond())
//格式化时间
time.Now().Format("2006-01-02 15:04")
//字符串转时间格式
t, err := time.Parse("2006-01-02 15:04:05", "2019-05-20 18:30:50")
//时间戳转为字符串
t := time.Unix("1558348250", 0).Format("2006-01-02 15:04")
```
#### 设置时区

```plain
//在windows系统上，没有安装go语言环境的情况下，time.LoadLocation会加载失败。
var sh, _ = time.LoadLocation("Asia/Shanghai")
time.Now().In(sh).Format("2006-01-02 15:04:05")
//time.FixedZone各个系统都能很好的设置时区
time.Now().In(time.FixedZone("CST", 8*3600)).Format("2006-01-02 15:04:05"))

```

## 

### **strconv**

包strconv主要实现对字符串和基本数据类型之间的转换。

基本数据类型包括：布尔、整型（包括有/无符号、二进制、八进制、十进制和十六进制）和浮点型等。

常用：

```
字符串转换为整型：
func ParseInt(s string, base int, bitSize int) (i int64, err error)
func ParseUint(s string, base int, bitSize int) (n uint64, err error)
func Atoi(s string) (i int, err error)
Atoi内部调用ParseInt(s,10,0)实现
参数 base 代表字符串按照给定的进制进行解释，一般base 的取值为 2~36。
如果 base 的值为 0，则会根据字符串的前缀来确定 base 的值：
"0x" 表示 16 进制； "0" 表示 8 进制；否则就是 10 进制。
参数 bitSize 表示的是整数取值范围，或者说整数的具体类型。
取值 0、8、16、32 和 64 分别代表 int、int8、int16、int32 和 int64。
i 则表示bitSize 能够表示的最大或最小值

整数转字符串：
func FormatUint(i uint64, base int) string 无符号整型转字符串
func FormatInt(i int64, base int) string  有符号整型转字符串
func Itoa(i int) string
Itoa 内部直接调用 FormatInt(i, 10) 实现的。
base 参数可以取 2~36（0-9，a-z）。

整数转为字符数组
func AppendInt(dst []byte, i int64, base int) []byte
func AppendUint(dst []byte, i uint64, base int) []byte
将整数转为字符数组 append 到目标字符数组中
```

```
字符串转bool：
func ParseBool(str string) (value bool, err error)
接受 1, t, T, TRUE, true, True, 0, f, F, FALSE, false, False 等字符串；
其他形式的字符串会返回错误
func FormatBool(b bool) string
直接返回 "true" 或 "false"
func AppendBool(dst []byte, b bool)
将 "true" 或 "false" append 到 dst 中
这里用了一个 append 函数对于字符串的特殊形式：append(dst, "true"...)
```

## 
```
字符串和浮点：
func FormatFloat(f float64, fmt byte, prec, bitSize int) string
FormatFloat 将浮点数 f 转换为字符串形式
f：要转换的浮点数
fmt：格式标记（b、e、E、f、g、G）
prec：精度（数字部分的长度，不包括指数部分）
bitSize：指定浮点类型（32:float32、64:float64），结果会据此进行舍入。

格式标记：
'b' (-ddddp±ddd，二进制指数)
'e' (-d.dddde±dd，十进制指数)
'E' (-d.ddddE±dd，十进制指数)
'f' (-ddd.dddd，没有指数)
'g' ('e':大指数，'f':其它情况)
'G' ('E':大指数，'f':其它情况)

如果格式标记为 'e'，'E'和'f'，则 prec 表示小数点后的数字位数
如果格式标记为 'g'，'G'，则 prec 表示总的数字位数（整数部分+小数部分）
参考格式化输入输出中的旗标和精度说明



func ParseFloat(s string, bitSize int) (float64, error)
将字符串解析为浮点数，使用 IEEE754 规范进行舍入。
bigSize 取值有 32 和 64 两种，表示转换结果的精度。
如果有语法错误，则 err.Error = ErrSyntax
如果结果超出范围，则返回 ±Inf，err.Error = ErrRange

func AppendFloat(dst []byte, f float64, fmt byte, prec int, bitSize int)
```

## 
## 文件操作

### 打开关闭文件

```
os.Open()以只读方式打开文件
os.Close()
```
### 读取文件

```
<1>read
<2>bufio    
```
### 文件写入

```
os.Openfile()
file, err := os.OpenFile("xx.txt", os.O_CREATEos.O_WRONLY, 0666)
```
| 模式          | 含义   |
|:------------|:-----|
| os.O_WRONLY | 只写   |
| os.O_CREATE | 创建文件 |
| os.O_RDONLY | 只读   |
| os.O_RDWR   | 读写   |
| os.O_TRUNC  | 清空   |
| os.O_APPEND | 追加   |

```
<1>Write/WriteString
<2>bufio.NewWriter
```
# go web

## url

```
url(Uniform Resource Locator)统一资源定位符，由一串简单文本字符组成。
Url结构：Scheme://Login:password@Address:port/path/to/resource?query_string#fragment
Scheme: 协议，如http,https,ftp等
Login:password@: 身份验证
Address: 服务器地址
Port: 服务器端口
/path/to/resource: 文件路径
?query_string: 查询字符串
#fragment: 片段ID，如http页面中内部的标签
"https://xiaoming:123456@www.example.com:8080/resource/level/next?file=got.rar&timestamp=123432#temp"
```
## http.request




**请求报文结构:**

HTTP请求报文包含三部分:

| 报文组成 | 名称	            | 描述                                        |
|:-----|:---------------|:------------------------------------------|
| 请求行  | request line   | 包含请求方法、URL、HTTP版本，定义了客户端与服务器交互的请求方法。      |
| 请求头	 | request header | 包含HTTP请求首部字段                              |
| 请求体  | request body   | 请求主体或实体，GET请求无提交表单数据请求实体为空，POST请求则包含表单数据。 |

**http.Request**

net/http包封装了http.Request结构体表示HTTP请求报文，用于获取一次HTTP请求的所有信息。

```
type Request struct {
 Method string// 请求方法
 URL *url.URL// 请求地址
 Proto      string // 协议版本 "HTTP/1.0"
 ProtoMajor int    // 1 协议主版本
 ProtoMinor int    // 0 协议次版本
 Header Header// 请求头
 Body io.ReadCloser// 请求体
 GetBody func() (io.ReadCloser, error)// 获取请求体
 ContentLength int64// 内容长度
 TransferEncoding []string// 传输编码
 Close bool// 连接是否关闭
 Host string// 服务器主机地址
 Form url.Values// GET表单
 PostForm url.Values// POST表单
 MultipartForm *multipart.Form// 上传表单
 Trailer Header
 RemoteAddr string// 远程客户端地址
 RequestURI string// 请求URI
 TLS *tls.ConnectionState// HTTPS
 Cancel <-chan struct{}
 Response *Response// 响应
 ctx context.Context// 上下文对象
}
```
| 字段	            | 说明                                                   |
|:---------------|:-----------------------------------------------------|
| Method	<br>    | 请求方法，可选GET、POST、PUT等。若客户端请求方法为空字符串则默认为GET请求。         |
| URL	           | 用于指定被请求的服务端请求URI或客户端请求访问的URL，对客户端来说用于记录要连接的服务端地址。    |
| Proto	         | 协议版本                                                 |
| Header	        | 请求头                                                  |
| Body	          | 请求体，若为空则表示GET请求。                                     |
| ContentLength	 | 请求体字节大小，若等于0则请求体body为空可表示为unknown，若等于-1也可以表示unknown。 |
| Form	          | 表单字段                                                 |

例如：获取HTTP请求信息

```
func main() {
 //注册路由
 http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
  fmt.Printf("Proto: %+v\n", r.Proto)
  fmt.Printf("ProtoMajor: %+v\n", r.ProtoMajor)
  fmt.Printf("ProtoMinor: %+v\n", r.ProtoMinor)
  fmt.Printf("URL: %+v\n", r.URL)
  fmt.Printf("RequestURI: %+v\n", r.RequestURI)
  fmt.Printf("RemoteAddr: %+v\n", r.RemoteAddr)
  fmt.Printf("Host: %+v\n", r.Host)
  fmt.Printf("Method: %+v\n", r.Method)
  fmt.Printf("ContentLength: %+v\n", r.ContentLength)
 })
 //监听端口接收连接
 if err := http.ListenAndServe(":8900", nil); err != nil {
  panic(err)
 }
}
```

```
Proto: HTTP/1.1
ProtoMajor: 1
ProtoMinor: 1
URL: /
RequestURI: /
RemoteAddr: 127.0.0.1:8110
Host: 127.0.0.1:8900
Method: GET
ContentLength: 0
```
**http.Header**
请求头和响应头都通过Header类型标识

```
type Header map[string][]string
```
http.Header是一个键值对字典，键是字符串，值是字符串切片。
http.Header提供了增删改查方法用于对请求进行读取和设置

Header对象提供Get()可通过传入对应的字段名获取值，用户读取或打印请求头字段值。

```
func (h Header) Get(key string) string {
 return textproto.MIMEHeader(h).Get(key)
}
```
例如：在浏览器中打印请求头中User-Agent字段的值
```
http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
str := r.Header.Get("User-Agent")
w.Write([]byte(str))
})
http.ListenAndServe(":8080", nil)
output:
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.
```

