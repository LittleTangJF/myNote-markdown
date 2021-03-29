```nginx
rpm -ql nginx //查看nginx的安装目录

ps aux | grep nginx //查看任务

nginx或systemctl start nginx.service //启动nginx
nginx -s quit或 nginx -s stop 或 systemctl stop nginx.service                                     //停止nginx
systemctl restart nginx.service         // 重启nginx
nginx -s reload      //修改配置文件使用重载快速生效

netstat -tlnp      //查看端口号使用情况
```

### 例子

- ```nginx
  // nginx.conf
  http {
    include mime.types; 
    #nginx开启gzip
    #前端文件在build的时候已经配置好压缩,需要再配置一下nginx;
    gzip on; 
    gzip_static on;
    gzip_buffers 4 16k;
    gzip_comp_level 5;
    gzip_types text/plain application/javascript text/css application/xml text/javascript application/x-httpd-php image/jpeg 
                image/gif image/png;
    
    #nginx请求级别配置
    server {
      listen       80;
      server_name  www.genal.fun;
      location / {
        root   html;
        index  index.html index.htm;
        add_header Cache-Control public;
      }
  
      location ^~/api/ {
        rewrite ^/api/(.*) /$1 break;
        proxy_pass http://localhost:3000;
      }
  
      location ^~/socket.io/ {
        proxy_pass http://localhost:3000;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
      }
      error_page   500 502 503 504  /50x.html;
      location = /50x.html {
          root   html;
      }
    }  
  }
  ```

  