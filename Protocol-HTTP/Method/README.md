# Http Method

* [POST](POST.md)
* [GET]()
* [PUT]()
* [DELETE]()

## POST vs GET
```md
GET在浏览器回退时是无害的，而POST会再次提交请求。
GET产生的URL地址可以被Bookmark，而POST不可以。
GET请求会被浏览器主动cache，而POST不会，除非手动设置。
GET请求只能进行url编码，而POST支持多种编码方式。
GET请求参数会被完整保留在浏览器历史记录里，而POST中的参数不会被保留。
GET请求在URL中传送的参数是有长度限制的，而POST么有。
对参数的数据类型，GET只接受ASCII字符，而POST没有限制。
GET比POST更不安全，因为参数直接暴露在URL上，所以不能用来传递敏感信息。
GET参数通过URL传递，POST放在Request body中。
```
```md
GET和POST本质上就是TCP链接，并无差别。
但是由于HTTP的规定和浏览器/服务器的限制，导致他们在应用过程中体现出一些不同。
```
* GET产生一个TCP数据包；POST产生两个TCP数据包。
```md
对于GET方式的请求，浏览器会把http header和data一并发送出去，服务器响应200（返回数据）
对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）。
```
* * 看起来GET比POST更有效?
```md
因此Yahoo团队有推荐用GET替换POST来优化网站性能。但这是一个坑！跳入需谨慎。为什么?
1. GET与POST都有自己的语义，不能随便混用。
2. 据研究，在网络环境好的情况下，发一次包的时间和发两次包的时间差别基本可以无视。
    而在网络环境差的情况下，两次包的TCP在验证数据包完整性上，有非常大的优点。
3. 并不是所有浏览器都会在POST中发送两次包，Firefox就只发送一次。
```

## 幂等性 Idempotence
```md
HTTP方法的幂等性是指一次和多次请求某一个资源应该具有同样的副作用。
幂等性属于语义范畴，正如编译器只能帮助检查语法错误一样，HTTP规范也没有办法通过消息格式等语法手段来定义它，
这可能是它不太受到重视的原因之一。
但实际上，幂等性是分布式系统设计中十分重要的概念，而HTTP的分布式本质也决定了它在HTTP中具有重要地位。
```
[理解HTTP幂等性](https://www.cnblogs.com/weidagang2046/archive/2011/06/04/idempotence.html)
