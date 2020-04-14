# [Websocketd](http://websocketd.com/)

利用 Websocketd 可以非常轻松地构建支持 WebSocket 的应用程序。

只要编写一个读取STDIN并写入STDOUT的可执行程序，就可以构建一个WebSocket服务器。
可以用 Python，Ruby，Perl，Bash，.NET，C，Go，PHP，Java，Clojure，Scala，
Groovy，Expect，Awk，VBScript，Haskell，Lua，R等实现，不需要网络库。

它的最大特点，就是后台脚本不限语言，
标准输入（stdin）就是 WebSocket 的输入，标准输出（stdout）就是 WebSocket 的输出。

Websocketd 的实质，就是命令行的 WebSocket 代理。
只要命令行可以执行的程序，都可以通过它与浏览器进行 WebSocket 通信。

## [Examples](https://github.com/joewalnes/websocketd/tree/master/examples)
### count.sh
```sh
#!/bin/bash
for ((COUNT = 1; COUNT <= 10; COUNT++)); do
  echo $COUNT
  sleep 1
done
```
```sh
$ chmod +x count.sh
$ brew install websocketd
```
```sh
$ websocketd --port=8081 ./count.sh
Fri, 08 Mar 2019 15:38:50 +0800 | INFO   | server     |  | Serving using application   : ./count.sh
Fri, 08 Mar 2019 15:38:50 +0800 | INFO   | server     |  | Starting WebSocket server   : ws://localhost:8081/
```
* count.html
```html
<!DOCTYPE html>
<pre id="log"></pre>
<script>
  // helper function: log message to screen
  function log(msg) {
    document.getElementById('log').textContent += msg + '\n';
  }

  // setup websocket with callbacks
  var ws = new WebSocket('ws://localhost:8081/');
  ws.onopen = function() {
    log('CONNECT');
  };
  ws.onclose = function() {
    log('DISCONNECT');
  };
  ws.onmessage = function(event) {
    log('MESSAGE: ' + event.data);
  };
</script>
```
### file:///Users/count.html

CONNECT
MESSAGE: 1
MESSAGE: 2
MESSAGE: 3
MESSAGE: 4
MESSAGE: 5
MESSAGE: 6
MESSAGE: 7
MESSAGE: 8
MESSAGE: 9
MESSAGE: 10
DISCONNECT

Fri, 08 Mar 2019 15:45:34 +0800 | ACCESS | session    | url:'http://localhost:8081/' id:'1552031134001325754' remote:'::1' command:'./count.sh' origin:'file://' | CONNECT
Fri, 08 Mar 2019 15:45:44 +0800 | ACCESS | session    | url:'http://localhost:8081/' id:'1552031134001325754' remote:'::1' command:'./count.sh' origin:'file://' pid:'94152' | DISCONNECT

## Utility
### [Web VMStat](https://github.com/joewalnes/web-vmstats)

Display live Linux system stats (memory, CPU, IO, etc) in a pretty web-page, with charts and everything.
在漂亮的网页中显示实时Linux系统统计信息（内存，CPU，IO等），包括图表和所有内容。

这是一个很小的应用程序，使用websocketd通过WebSocket流式传输这些统计信息，并使用SmoothieCharts对其进行绘制。



