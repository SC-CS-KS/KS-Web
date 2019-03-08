# Nginx 正向代理
```md
	如果把局域网外的Internet想象成一个巨大的资源库，则局域网中的客户端要访问Internet，则需要通过代理服务器来访问，这种代理服务就称为正向代理。
	server {  
    resolver 192.168.1.1; #指定DNS服务器IP地址  
    listen 8080;  
    location / {  
        proxy_pass http://$http_host$request_uri; #设定代理服务器的协议和地址  
    }  
} 
	在该server块中，不要出现server_name指令，即不要设置虚拟主机的名称和IP。
	而resolver是必需的，如果没有该指令，nginx无法处理接收到的域名。
	其次，nginx代理服务不支持正向代理HTTPS站点。
	们在浏览器中设置代理服务：“Internet选项” -> “连接” -> “局域网设置” -> “代理服务器”
```