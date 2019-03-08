# Nginx Reverse Proxy
```md
	反向代理（Reverse Proxy）
		以代理服务器来接受internet上的连接请求，然后将请求转发给内部网络上的服务器，并将从服务器上得到的结果返回给internet上请求连接的客户端。
	proxy
		        location / {
            proxy_pass http://localhost:8080;
            proxy_set_header Host $host:$server_port;
        }
```