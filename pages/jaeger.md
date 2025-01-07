# 前世
	- ## Jaeger背景:
		- Jaeger的实现遵循的是OpenTracing规范，什么是OpenTracing规范？
		  OpenTracing制定了一套平台无关、厂商无关的Trace协议，使得开发人员能够方便的添加或更换分布式追踪系统的实现，早在近十年前就已经制定；与它相关的还有谷歌的OpenCensus，还有两者合并后的OpenTelemetry；
- # Jaeger与Zipkin
	- Jaeger 是Uber公司研发，后来贡献给CNCF的一个分布式链路追踪软件；
	  另外对标Jaeger的还有一个软件是Zipkin，由谷歌Dapper论文启发，Twitter开发，现在有专门团队维护，需要注意的是，Zipkin比Jaeger开发的早，前者在2012启动，Jaeger第一个正式版本发布于2017年，不过两者目前在Github上的star数量相差不多；
	- Jaeger属于后起之秀，架构方面也是参考了Zipkin的设计，没有太大差别，而目前两者的差距也是逐渐缩小。
	  另外，两者都支持仅内存方式存储数据，方便搭建测试环境。