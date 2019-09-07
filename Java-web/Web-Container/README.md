# Web Container
```md
一种是独立的Java Web容器，在这种容器里面只能运行Web程序，这种容器一般也叫做Web服务器
一种是与其他java ee容器混合在一起的Web容器
	Web容器负责运行Web程序，其他容器负责运行EJB等程序
```

## Impelement
* Tomcat
* Jetty
* Undertow
* Grizzly
* Tomcat
```md
Tomcat是一个免费的开放源代码的Servlet容器。
Tomcat和IIS、Apache等Web服务器一样，具有处理HTML页面的功能，
另外它还是一个Servlet和JSP容器，独立的Servlet容器是Tomcat的默认模式
不过，Tomcat处理静态HTML的能力不如Apache，我们可以将Apache和Tomcat集成在一起使用，Apache作为HTTP Web服务器，Tomcat作为Web容器
```
* WebLogic
```md
是用于开发、集成、部署和管理大型分布式Web应用、网络应用和数据库应用的Java应用服务器。
将Java的动态功能和Java Enterprise标准的安全性引入大型网络应用的开发、集成、部署和管理之中。
```
* JBoss
```
	背景
		是全世界开发者共同努力的成果，一个基于J2EE的开放源代码的应用服务器。 因为JBoss代码遵循LGPL许可，你可以在任何商业应用中免费使用它，而不用支付费用。JBoss支持EJB 1.1和EJB 2.0 EJB3.0的规范，它是一个管理EJB的容器和服务器。
		JBoss的目标是一个源代码开放的J2EE环境。但是JBoss核心服务仅是提供EJB服务器。JBoss不包括serverlers/JSP page 的WEB容器，当然可以和Tomcat或Jetty绑定使用。
	优点
		1、JBoss是免费的，开放源代码J2EE的实现，它通过LGPL许可证进行发布。
		2、JBoss需要的内存和硬盘空间比较小。
		3、安装非常简单。先解压缩JBoss打包文件再配置一些环境变量就可以了。
		4、JBoss能够"热部署"，部署BEAN只是简单拷贝BEAN的JAR文件到部署路径下就可以了。如果没有加载就加载它；如果已经加载了就卸载掉，然后LOAD这个新的。
		5、JBoss与Web服务器在同一个Java虚拟机中运行，Servlet调用EJB不经过网络，从而大大提高运行效率，提升安全性能。
		6、用户可以直接实施J2EE-EAR，而不是以前分别实施EJB-JAR和Web-WAR，非常方便。
```
### 比较
```md
1. JBoss 是 J2EE 应用服务器，而 Tomcat 只是一个 Servlet 容器，或者说是一个简单的 J2EE 应用服务器。
	 JBoss 中的 Servlet 容器还是 Tomcat。
	 与 Tomcat 类似的 Servlet 容器有：Jetty（开源）, Resin（开源）……。
	 与 JBoss 类似的 J2EE 应用服务器有：Glassfish（开源）, Geronimo（开源）, WebLogic（商业）, WebSphere（商业）
2. tomcat 是 JSP/Servlet 容器
		jboss 是 JEE 容器，JEE 包括JSP/Servlet，JMS， EJB，JAX-WS，JAX-RS，CDI等等，
		tomcat是完全开源，开源社区维护器产品更新
		jboss有开源和企业化两个版本，企业化被Red Hat支持，一般支持10年，产品后继有保障
3. 注意JBoss和tomcat是不一样，JBoss是一个可伸缩的服务器平台，
			当你的EJB程序编制完成后，如果访问量增加，只要通过增加服务器硬件就可以实现多台服务器同时运算，提高了负载容量，
      这个性能容量理论上是没有限制的，理论上无最大支持在线人数的上限，对于JBoss/EJB这样的平台来说，无最大访问量限制一说。
			这是JBoss/EJB不同于Spring /Tomcat等平台的最大优点所在，而且EJB 3.0也将出现轻量化解决方案，
      其实随着发展，已经模糊了轻量/重量的区别，如果还是以轻量/重量作为架构选择的标准，无疑是不明智的。
		可伸缩性应该是架构选择的主要标准，所谓可伸缩性，只在小型系统、一台服务器情况下，我的系统也可以良好运转，
    多台服务器扩展后，我的系统只需通过增加硬件就可以实现性能扩展，无需修改太多软件。
```
[Tomcat vs Jetty vs Grizzly vs Undertow](https://menelic.com/2016/01/06/java-rest-api-benchmark-tomcat-vs-jetty-vs-grizzly-vs-undertow/)
[Undertow,Tomcat和Jetty服务器配置详解与性能测试](https://www.cnblogs.com/maybo/p/7784687.html)