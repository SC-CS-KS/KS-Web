# What Is WebSocket ?
```md
是为了满足基于 Web 的日益增长的实时通信需求而产生的。
在传统的 Web 中，要实现实时通信，通用的方式是采用 HTTP 协议不断发送请求。
但这种方式即浪费带宽（HTTP HEAD 是比较大的），又消耗服务器 CPU 占用（没有信息也要接受请求）。
```
```md
WebSocket协议是一种双向通信协议，它建立在TCP之上。
```
## Usage Scenario
* [为什么引入WebSocket协议](https://blog.csdn.net/yl02520/article/details/7298309)

## Utility
```md
目前流行的浏览器都支持这个协议，例如Chrome，Safari，Firefox，Opera，IE等等
```

## Compare With
* vs. [Http](../http/README.md)
```md
WebSocket是一种双向通信协议，在建立连接后，WebSocket服务器和Browser/UA都能主动的向对方发送或接收数据，
就像Socket一样，不同的是WebSocket是一种建立在Web基础上的一种简单模拟Socket的协议。

HTTP、WebSocket 等应用层协议，都是基于 TCP 协议来传输数据的。

1. WebSocket 是 HTML5 中的协议，支持持久连接；而 Http 协议不支持持久连接。
2. WebSocket 在建立握手连接时，数据是通过http协议传输的。
```
* vs. [Socket](https://github.com/SunnnyChan/sc.cs-notes/tree/master/computer/network/socket)
```md
WebSocket 是一个完整的 应用层协议，包含一套标准的 API。
Socket 不是协议，是应用层与TCP/IP协议族通信的中间软件抽象层，它是一组接口。
```
* vs. HTML5
```md
WebSocket API 是 HTML5 标准的一部分， 
但这并不代表 WebSocket 一定要用在 HTML 中，或者只能在基于浏览器的应用程序中使用。
实际上，许多语言、框架和服务器都提供了 WebSocket 支持。
```