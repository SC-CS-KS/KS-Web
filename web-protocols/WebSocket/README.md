# [WebSocket](http://www.websocket.org/)
```md
是一种通过单个TCP连接提供全双工通信通道的Web技术。
```
## [What Is](WhatIs.md)

## [Protocol](protocol/README.md)
* [RFC6455](https://tools.ietf.org/html/rfc6455)

## Design
* 建立连接
* 进行通信
> * 服务端解析 WebSocket 报文
> * 服务端发送 WebSocket 报文

## Develop

## WebSocket API
### [Java](https://docs.oracle.com/javaee/7/tutorial/websocket.htm)
* javax.websocket
```md
JSR356 的 WebSocket 规范使用 javax.websocket.*的 API，
可以将一个普通 Java 对象（POJO）使用 @ServerEndpoint 注释作为 WebSocket 服务器的端点。
```

## Debug
* [Chrome Developer Tools](web-dev/debug/chrome/README.md)

## Implement

### [Browser Support for WebSockets](https://caniuse.com/#feat=websockets)

### WebSockets on the Server
* [Websocketd](implement/Websocketd.md)
```md
Websocketd 是一个小型命令行工具，它将包装现有的命令行界面程序，并允许通过WebSocket访问它。
```
* [µWebSockets](https://github.com/uNetworking/uWebSockets)
```md
适用于C ++ 11和Node.js的高度可扩展的WebSocket服务器和客户端实现。
```
* [jsonrpc-bidirectional](https://github.com/bigstepinc/jsonrpc-bidirectional)
```md
此项目的主要目标是让JSON-RPC服务器和客户端通过单个WebSocket连接支持双向JSON-RPC请求。
```
* [Cowboy](https://github.com/ninenines/cowboy)
```md
Cowboy是一个小型，快速和现代的HTTP服务器，用于Erlang/OTP，支持WebSocket。
```
* C++: libwebsockets
```md
LibWebSockets 采用C/C++语言编写，可定制化的力度更大，从TCP监听开始到封包的完成我们都可以参与编程。
```
* Erlang: Shirasu.ws

* Java: Jetty
* [Node.JS: ws](https://github.com/websockets/ws)
* [Node.JS: WebSocket-Node](https://github.com/theturtle32/WebSocket-Node)
* Node.JSµ: WebSockets
* [Node.JS: SocketCluster](https://socketcluster.io)
```md
SocketCluster是Node.js的开源实时框架。
它支持直接客户端 - 服务器通信和通过pub / sub通道的组通信。
它旨在轻松扩展到任意数量的进程/主机，是构建聊天系统的理想选择。
```
* [Node.JS: Socket.IO](https://socket.io/)
```md
最受欢迎的是socket.io，这是一个提供跨浏览器回退的Node.JS库。
```
* Ruby: em-websocket
* Python: PyWebSocket 
```md
采用 Python 语言编写，可以很好的跨平台，扩展起来也比较简单，
目前 WebKit 采用它搭建 WebSocket 服务器来做 LayoutTest。s
```
* Python: Tornado
* [PHP: Ratchet](http://socketo.me/)
```md
Ratchet是一个松散耦合的PHP库，为开发人员提供了通过WebSockets在客户端和服务器之间创建实时双向应用程序的工具。
```
* PHP: phpws

***[WebSocket API Tools](https://developer.mozilla.org/en-US/docs/Web/API/Websockets_API)***

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
