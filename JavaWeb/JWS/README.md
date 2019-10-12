# JWS

```md
java remote service
	在各个java类（包括ejb类）之间传递消息的中间件
	好比给我们送信的邮递员，在各个人之间收发信件
支持两种消息模型P2P和pub/stub，即点对点和发布订阅模型。
JMS 一般只是一个点发出一个Message到Message Server
优点
	支持异步通信、消息produce和recept松耦合。
RMI和JMS
	传输方式上
		 JMS 与 RMI 的区别在于，采用 JMS 服务，对象是在物理上被异步从网络的某个 JVM 上直接移动到另一个 JVM 上。
		RMI 对象是绑定在本地 JVM 中，只有函数参数和返回值是通过网络传送的
	方法调用上
		RMI一般都是同步的，也就是说，当client调用Server的一个方法的时候，需要等到对方的返回，
    才能继续执行client端，这个过程调用本地方法感觉上是一样的，这也是RMI的一个特点。
		JMS 一般只是一个点发出一个Message到Message Server,发出之后一般不会关心谁用了这个message。
    一般RMI的应用是紧耦合，JMS的应用相对来说是松散耦合应用。
```
```md
是指与webservice相关的J2EE技术叫做 JWS
指的就是 java web service
```

* JAX-RPC
```md
已有的Java类或Java应用都能够被重新包装
	并以Web Services的形式发布。
JAX-RPC提供了将RPC参数（in/out）编码和解码的API，
使开发人员可以方便地使用SOAP消息来完成RPC 调用，EJB应用也可以使用JAX-RPC来包装成Web服务。
```

* SOAP
```md
（SOAP with Attachemnts API for Java）
是JAX-RPC的一个增强，为进行低层次的SOAP消息操纵提供了支持。
```

* JAXR
```md
（Java API for XML Registries）提供了与多种类型注册服务进行交互的API。
JAXR运行客户端访问与JAXR规范相兼容的Web Servcices，这里的Web Services即为注册服务。
一般来说，注册服务总是以Web Services的形式运行的。
```

* JAX-WS
```md
Java API forXML-Based Web Services 
规范是一组XML web services的JAVA API
在jdk1.6之后就有了自带的实现，
	但是这种实现是比较简单的，基本上就只能够传递SOAP协议格式的消息
JAX-WS允许开发者可以选择RPC-oriented或者message-oriented 来实现自己的web services。
```
```md
支持JAX-WS服务规范的框架有：CXF，Axis，Xfile
```
