# [WebSocket](https://tools.ietf.org/html/rfc6455)

## [What Is](WhatIs.md)

## Design
* 建立连接
* 进行通信
> * 服务端解析 WebSocket 报文
> * 服务端发送 WebSocket 报文

* [Message](Message.md)

## Develop
## Debug
* [Chrome Developer Tools](web-dev/debug/chrome/README.md)

## Implement
### Server
* [Websocketd](Websocketd.md)
```md
Websocketd 是一个小型命令行工具，它将包装现有的命令行界面程序，并允许通过WebSocket访问它。
```
#### [Java](https://docs.oracle.com/javaee/7/tutorial/websocket.htm)
* javax.websocket
```md
JSR356 的 WebSocket 规范使用 javax.websocket.*的 API，
可以将一个普通 Java 对象（POJO）使用 @ServerEndpoint 注释作为 WebSocket 服务器的端点。
```
#### Python
* PyWebSocket 
```md
采用 Python 语言编写，可以很好的跨平台，扩展起来也比较简单，
目前 WebKit 采用它搭建 WebSocket 服务器来做 LayoutTest。s
```
#### Node 
* [WebSocket-Node](https://github.com/theturtle32/WebSocket-Node)
* µWebSockets
* Socket.IO

#### C/C++
* LibWebSockets
```md
LibWebSockets 采用C/C++语言编写，可定制化的力度更大，
从TCP监听开始到封包的完成我们都可以参与编程。
```

## Framework
* [八种 WebSocket 框架](http://sdds-gov-cn.iocoder.cn/Fight/Performance-comparison-of-eight-WebSocket-frameworks/)
```md
2.1 Netty
2.2 Vert.x
2.3 Undertow
2.4 Jetty
2.5 Grizzly
2.6 Spray
2.7 Node.js
2.8 Go
```
## Resources
* [WebSocket 实战](https://www.ibm.com/developerworks/cn/java/j-lo-WebSocket/index.html)
