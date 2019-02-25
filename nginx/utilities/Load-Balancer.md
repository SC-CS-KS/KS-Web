# Nginx Load Balancer

```md
	RR（默认）
		每个请求按时间顺序逐一分配到不同的后端服务器，如果后端服务器down掉，能自动剔除。
		　　upstream test {
        server localhost:8080;
        server localhost:8081;
    }
			    server {
        listen       81;                                                        
        server_name  localhost;                                              
        client_max_body_size 1024M;
 
        location / {
            proxy_pass http://test;
            proxy_set_header Host $host:$server_port;
        }
    }
	权重
		 指定轮询几率，weight和访问比率成正比，用于后端服务器性能不均的情况。
		　　upstream test {
        server localhost:8080 weight=9;
        server localhost:8081 weight=1;
    }
	ip_hash
		iphash的每个请求按访问ip的hash结果分配，这样每个访客固定访问一个后端服务器，可以解决session的问题。
		　　upstream test {
        ip_hash;
        server localhost:8080;
        server localhost:8081;
    }
	fair（第三方）
		按后端服务器的响应时间来分配请求，响应时间短的优先分配。
		 　　upstream backend {
        fair;
        server localhost:8080;
        server localhost:8081;
    }
	url_hash（第三方）
		按访问url的hash结果来分配请求，使每个url定向到同一个后端服务器，后端服务器为缓存时比较有效。
		在upstream中加入hash语句，server语句中不能写入weight等其他的参数，hash_method是使用的hash算法。
		　　upstream backend {
        hash $request_uri;
        hash_method crc32;
        server localhost:8080;
        server localhost:8081;
    }
```