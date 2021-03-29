# docker

- ### Container-容器

- ### Image-镜像

## 开始

- ### 配置镜像 -docker Engine

  - ```json
    "registry-mirrors": [
        "http://f1361db2.m.daocloud.io"
      ]
    ```

## 安装

- ### mysql

  - 拉取pull

  ### 

## 命令行

- ### docker

  - docker  -v / info
  
  - docker  images    镜像
  
  - docker  ps   -a      容器        对比 ps aux | grep nginx
  
  - docker rm -f webserver`命令来移除正在运行的容器
  
  - docker list` 列出本地镜像
  
  - docker rmi` 删除的镜像
  
  - -p: 指定端口映射
  
  - -d: 后台运行
  
  - --name: 指定容器的名字
  
  - exec: 进入容器 docker container exec -it ID 
  
  - rmi: 删除镜像
  
  - stop: 停止服务        对比 nginx -s stop
  
  - rm：删除容器
  
  - netstat -ntulp | grep 8089 查看端口占用
  
    

### nginx

启动nginx容器：docker run --name nginx1 -p 3333:80 -d nginx

1. 创建www目录 mkdir -p   /server/nginx/www -容器中目录/usr/share/nginx/html

2. logs日志   /server/nginx/logs   -容器中目录/var/log/nginx

3. conf配置  /server/nginx/conf   -容器中目录/etc/nginx/nginx.conf

4. 虚拟主机 /server/nginx/conf.d

5. copy配置   docker cp 80aec0276696:/etc/nginx/nginx.conf ~/server/nginx/conf

6. 删除临时镜像  docker rm -f ID

7. 映射到本地   

   1. ```
      docker run  -d -p 9000:80 --name nignx -v ~/server/nginx/www:/usr/share/nginx/html -v ~/server/nginx/conf/nginx.conf:/etc/nginx/nginx.conf -v ~/server/nginx/logs:/var/log/nginx nginx
      ```

      

- 写一个Dckerfile
- 使用docker image build 将Dockerfile 打包成镜像
- 使用docker container create 来根据镜像创建容器
- 使用docker container start 来启动一个创建好的容器

### nginx代理

#### 	正向代理

- 客户端 ----> 代理 ----> 服务器

####     反向代理

- 客户端 -----> 代理<----> 服务器