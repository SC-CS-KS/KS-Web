# Servlet

## [WhatIs](WhatIs.md)

## Design
* Servlet生命周期
```md
(1) 加载和实例化
	如果Servlet容器还没实例化一个Servlet对象，此时容器装载和实例化一个 Servlet。
		创建出该 Servlet 类的一个实例。
		如果已经存在一个Servlet对象，此时不再创建新实例。
(2) 初始化
	在产生 Servlet 实例后，容器负责调用该 Servlet 实例的 init() 方法，在处理用户请求之前，来做一些额外的初始化工作。
(3) 处理请求
	当 Servlet 容器接收到一个 Servlet 请求时，便运行与之对应的 Servlet 实例的 service() 方法，
		service() 方法根据用户的请求调用相对应的doGet或doPost 方法来处理用户请求。
		然后再进入对应的方法中调用逻辑层的方法，实现对客户的响应。
(4) 销毁
	当 Servlet 容器决定将一个 Servlet 从服务器中移除时 ( 如 Servlet 文件被更新 )，便调用该 Servlet 实例的 destroy() 方法，在销毁该 Servlet 实例之前，来做一些其他的工作。
注意：
	(1)(2)(4) 在 Servlet 的整个生命周期中只会被执行一次
```
* Servlet单实例多线程模式

## Architecture

* ServletConfig
* ServletContext 
* ServletRequest
* ServletResponse

```md
交易场景就由 ServletContext 来描述，而定制的参数集合就由 ServletConfig 来描述
ServletRequest 和 ServletResponse 就是要交互的具体对象。它们通常都是作为运输工具来传递交互结果。
```

## Reference
* [Servlet 工作原理解析](https://www.ibm.com/developerworks/cn/java/j-lo-servlet/)

