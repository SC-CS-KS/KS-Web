# Message

* Request Headers
```http
GET ws://10.96.111.130:8081/ws HTTP/1.1
Host: 10.96.111.130:8081
Connection: Upgrade
Pragma: no-cache
Cache-Control: no-cache
Upgrade: websocket
Origin: http://10.96.111.130:8081
Sec-WebSocket-Version: 13
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.109 Safari/537.36
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en;q=0.8
Sec-WebSocket-Key: zDZ/E2myeYgoGbO1hLHQWw==
Sec-WebSocket-Extensions: permessage-deflate; client_max_window_bits
```

* Response Headers
```http
HTTP/1.1 101 Switching Protocols
Date: Friday, March 8, 2019 4:46:52 PM CST
Access-Control-Allow-Origin: http://10.96.111.130:8081
Access-Control-Allow-Credentials: true
Access-Control-Allow-Headers: authorization,Content-Type
Access-Control-Allow-Methods: POST, GET, OPTIONS, PUT, HEAD, DELETE
X-FRAME-OPTIONS: SAMEORIGIN
X-XSS-Protection: 1
Sec-WebSocket-Extensions: permessage-deflate
Connection: Upgrade
Sec-WebSocket-Accept: 51sbFernckDhcYaHbpe542qK848=
Server: Jetty(9.4.14.v20181114)
Upgrade: WebSocket
```
* Data
```json
{"op":"LIST_CONFIGURATIONS","principal":"anonymous","ticket":"anonymous","roles":"[\"anonymous\"]"}
```
```json
{"op":"PING","principal":"anonymous","ticket":"anonymous","roles":"[\"anonymous\"]"}
```
```json
{
"op":"RUN_PARAGRAPH",
"data":{
"id":"20190226-165409_698627529",
"paragraph":"sc.version\n",
"config":{
"colWidth":12,
"fontSize":9,
"enabled":true,
"results":{
},
"editorSetting":{
"language":"scala",
"editOnDblClick":false,
"completionKey":"TAB",
"completionSupport":true
},
"editorMode":"ace/mode/scala",
"tableHide":false
},
"params":{
}
},
"principal":"anonymous",
"ticket":"anonymous",
"roles":"[\"anonymous\"]"
}
```