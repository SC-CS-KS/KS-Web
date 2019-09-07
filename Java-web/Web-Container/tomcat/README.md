# Tomcat
```md
背景
	当初在Apache开发时还未出现Servlet的概念，所以Apache不能内置支持Servlet。
		实际上，除了Apache，其他许多Web服务器软件都不能直接支持Servlet。
	为了支持Servlet，通常要单独开发程序，这种程序一般称为服务器小程序容器（Servlet Container）
		有时也叫做服务器小程序引擎（Servlet Engine）
	它是Web服务器或应用程序服务器的一部分
		用于在发送的请求和响应之上提供网络服务
		解码基于MIME的请求，格式化基于MIME的响应
		它在Servlet的生命周期内包容和管理Servlet
		是一个实时运行的外壳程序
		运行时由Web服务器软件处理一般请求，并把Servlet调用传递给“容器”来处理。 
		Tomcat就是满足这种需要的JSP/Servlet引擎
Tomcat是一个免费的开放源代码的Servlet容器
	是Sun公司的JSP/Servlet的官方实现。
		由于有了Sun的参与和支持，最新的Servlet和JSP规范总是能在Tomcat中得到体现
		Tomcat 6支持最新的Servlet 2.5和JSP 2.1规范
Tomcat和IIS、Apache等Web服务器一样，具有处理HTML页面的功能
	不过，Tomcat处理静态HTML的能力不如Apache
	可以将Apache和Tomcat集成在一起使用，Apache作为HTTP Web服务器，Tomcat作为Web容器。
Servlet容器
	独立运行的Servlet容器
		在这种模式下，Servlet容器作为构成Web服务器的一部分而存在。
	内置的Servlet容器
		Servlet容器由Web服务器插件和Java容器两部分组成
		Web服务器插件需要在某个Web服务器内部地址空间中打开一个JVM（Java虚拟机）
			在此JVM上加载Java容器并运行Servlet。
		如果客户端调用Servlet，Web服务器插件首先获得此请求的控制并将它传递（使用JNI技术）给Java容器，然后Java容器把此请求交给Servlet来处理。
		这种方式运行速度较快，并且能够提供良好的性能，适用于单进程、多线程服务器，但是在伸缩性方面存在不足。
	外置的Servlet容器
		Servlet容器运行在Web服务器外部地址空间。
		先由Web服务器插件在某个Web服务器外部地址空间打开一个JVM（Java虚拟机）
			然后加载Java容器来运行Servlet。
		Web服务器插件和JVM之间使用IPC（进程间通信）机制（通常是TCP/IPSockets）。
		如果客户端调用Servlet，Web服务器插件首先获得此请求的控制并将它传递（使用IPCs技术）给Java容器
			然后Java容器把此请求交给Servlet来处理
		这种方式对客户端请求的处理速度不如内置Servlet那样快，但是在其他方面（如可伸缩性、稳定性等）具有优势。
	Tomcat其工作模式也分为上述3种
		所以Tomcat既可被用作独立运行的Servlet引擎（便于开发和调试）
		又可作为一个需要增强功能的Web服务器（如当前的Apache、IIS和Netscape服务器）插件
```
## 工作流程
```md
① 客户端（通常都是浏览器）访问Web服务器，发送HTTP请求。
② Web服务器接收到请求后，传递给Servlet容器。
③ Servlet容器加载Servlet，产生Servlet实例后，向其传递表示请求和响应的对象。
④ Servlet实例使用请求对象得到客户端的请求信息，然后进行相应的处理。
⑤ Servlet实例将处理结果通过响应对象发送回客户端，容器负责确保响应正确送出，同时将控制返回给Web服务器。
```

## [系统架构与设计模式](https://www.ibm.com/developerworks/cn/java/j-lo-tomcat1/index.html)
