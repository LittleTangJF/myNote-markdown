```nginx
rpm -ql nginx //查看nginx的安装目录

ps aux | grep nginx //查看任务

nginx或systemctl start nginx.service //启动nginx
nginx -s quit或 nginx -s stop 或 systemctl stop nginx.service                                     //停止nginx
systemctl restart nginx.service         // 重启nginx
nginx -s reload      //修改配置文件使用重载快速生效

netstat -tlnp      //查看端口号使用情况
```

