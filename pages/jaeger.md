# 前世
	- ## Jaeger背景:
		- Jaeger的实现遵循的是OpenTracing规范，什么是OpenTracing规范？
		  OpenTracing制定了一套平台无关、厂商无关的Trace协议，使得开发人员能够方便的添加或更换分布式追踪系统的实现，早在近十年前就已经制定；与它相关的还有谷歌的OpenCensus，还有两者合并后的OpenTelemetry；
- # Jaeger与Zipkin
	- Jaeger 是Uber公司研发，后来贡献给CNCF的一个分布式链路追踪软件；
	  另外对标Jaeger的还有一个软件是Zipkin，由谷歌Dapper论文启发，Twitter开发，现在有专门团队维护，需要注意的是，Zipkin比Jaeger开发的早，前者在2012启动，Jaeger第一个正式版本发布于2017年，不过两者目前在Github上的star数量相差不多；
- 一些对比如下(数据统计截止于本文发布时间)：
- Zipkin	Jaeger
  Stars	13.3K	11.4K
  发布时间	2012	2017
  开发语言	Java	Go
  issues opened	161	332
  versions-released	202	34
  last-release-time	2020-4-16	2020-6-19
  contributors	139	156
  official-supported-lang	C#, Go, Java, JS, Ruby, Scala, PHP	C#, C++, Go, Java, Node.js, Python
  official-docs	Zipkin-docs	Jaeger-docs
  backend-storage	Cassandra、ElasticSearch	Cassandra3.4+, ElasticSearch5.x/6.x/7.x
  上面列出的是官方支持的开发语言，两者都还有许多非官方支持的语言，在官网可以找到。
  Jaeger属于后起之秀，架构方面也是参考了Zipkin的设计，没有太大差别，而目前两者的差距也是逐渐缩小。
  另外，两者都支持仅内存方式存储数据，方便搭建测试环境。
  ————————————————
- 版权声明：本文为博主原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接和本声明。
                        
  原文链接：https://blog.csdn.net/sc_lilei/article/details/107834597