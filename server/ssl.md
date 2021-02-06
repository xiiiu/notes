#配置ssl证书
> 修改/etc/nginx/nginx.conf
```conf
    server {
        #listen       80 default_server;
        #listen       [::]:80 default_server;
        listen       443 ssl http2 default_server;
        listen       [::]:443 ssl http2 default_server;
        server_name  www.fozn.com;
        root         /usr/share/nginx/html;

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;
        ssl_certificate /etc/nginx/xxxx_www.fozn.com.pem;  #需要将cert-file-name.pem替换成已上传的证书文件的名称。
        ssl_certificate_key /etc/nginx/xxxx_www.fozn.com.key; #需要将cert-file-name.key替换成已上传的证书密钥文件的名称。
        ssl_session_timeout 5m;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4; #表示使用的加密套件的类型。
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2; #表示使用的TLS协议的类型。
        ssl_prefer_server_ciphers on;

        location / {
        }

        error_page 404 /404.html;
        location = /404.html {
        }

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
        }
    }
```
