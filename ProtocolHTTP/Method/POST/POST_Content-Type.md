# POST Content-Type 
```md
POST 提交数据方案，包含了 Content-Type 和消息主体编码方式两部分。
```
* application/x-www-form-urlencoded
```md
浏览器的原生 <form> 表单，如果不设置 enctype 属性，那么最终就会以 application/x-www-form-urlencoded 方式提交数据。
```
```http
POST http://www.example.com HTTP/1.1
Content-Type: application/x-www-form-urlencoded;charset=utf-8

title=test&sub%5B%5D=1&sub%5B%5D=2&sub%5B%5D=3
```
```md
首先，Content-Type 被指定为 application/x-www-form-urlencoded；
其次，提交的数据按照 key1=val1&key2=val2 的方式进行编码，key 和 val 都进行了 URL 转码。

大部分服务端语言都对这种方式有很好的支持。
例如 PHP 中，$_POST['title'] 可以获取到 title 的值，$_POST['sub'] 可以得到 sub 数组。

很多时候，我们用 Ajax 提交数据时，也是使用这种方式。
例如 JQuery 和 QWrap 的 Ajax，Content-Type 默认值都是「application/x-www-form-urlencoded;charset=utf-8」。
```

* multipart/form-data
```md
如果要发送大量的二进制数据（non-ASCII），"application/x-www-form-urlencoded" 显然是低效的，
因为它需要用 3 个字符来表示一个 non-ASCII 的字符。
因此，这种情况下，应该使用 "multipart/form-data" 格式。multipart/form-data 用以支持向服务器发送二进制数据。
```
```md
必须让 <form> 表单的 enctype 等于 multipart/form-data。
```
```http
POST http://www.example.com HTTP/1.1
Content-Type:multipart/form-data; boundary=----WebKitFormBoundaryrGKCBY7qhFd3TrwA

------WebKitFormBoundaryrGKCBY7qhFd3TrwA
Content-Disposition: form-data; name="text"

title
------WebKitFormBoundaryrGKCBY7qhFd3TrwA
Content-Disposition: form-data; name="file"; filename="chrome.png"
Content-Type: image/png

PNG ... content of chrome.png ...
------WebKitFormBoundaryrGKCBY7qhFd3TrwA--
```
```md
首先生成了一个 boundary 用于分割不同的字段，为了避免与正文内容重复，boundary 很长很复杂。
然后 Content-Type 里指明了数据是以 multipart/form-data 来编码，本次请求的 boundary 是什么内容。

消息主体里按照字段个数又分为多个结构类似的部分(多个 Part)，每部分都是以 --boundary 开始，
Part 头信息中必须包含一个 Content-Disposition 头，其他的头信息则为可选项， 比如 Content-Type 等。

Content-Disposition 包含了 type 和 一个名字为 name 的 parameter，type 是 form-data，
name 参数的值则为表单控件（也即 field）的名字，如果是文件，那么还有一个 filename 参数，值就是文件名。
如 ： Content-Disposition: form-data; name="user"; filename="hello.txt"

消息主体最后以 --boundary-- 标示结束。
```
> * 注意：
```md
如果文件内容是通过填充表单来获得，那么上传的时候，Content-Type 会被自动设置（识别）成相应的格式，
如果没法识别，那么就会被设置成 "application/octet-stream"
```
```md
如果多个文件被填充成单个表单项，那么它们的请求格式则会是 multipart/mixed。
```
```md
如果 Part 的内容跟默认的 encoding 方式不同，那么会有一个 "content-transfer-encoding" 头信息来指定。
```

**[rfc2388  Returning Values from Forms:  multipart/form-data](https://tools.ietf.org/html/rfc2388)**
* application/json
```md
用来告诉服务端消息主体是序列化后的 JSON 字符串。
```
```md
可以方便的提交复杂的结构化数据，特别适合 RESTful 的接口。
```
* text/xml
```md
XML-RPC 是一种使用 HTTP 作为传输协议，XML 作为编码方式的远程调用规范。
```
```http
POST http://www.example.com HTTP/1.1 
Content-Type: text/xml

<?xml version="1.0"?>
<methodCall>
    <methodName>examples.getStateName</methodName>
    <params>
        <param>
            <value><i4>41</i4></value>
        </param>
    </params>
</methodCall>
```