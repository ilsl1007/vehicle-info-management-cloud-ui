the UI fro vehicle-info-management-cloud
#### nginx.conf backup
```shell script
    upstream gatewayServer {
        server 172.18.120.171:9030;
        server 172.18.120.171:9031;
    }

    server {
        listen       8088;
        server_name  localhost;

        location / {
            root   html/spa;
            index  index.html index.htm;
        }

        location /api/ {
            proxy_pass  http://gatewayServer/;
        }

        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
    }
```