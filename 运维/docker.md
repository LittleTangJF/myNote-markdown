来源：https://www.lixian.fun/3812.html

## 一、Docker介绍

#### 1.1  引言

> 1. 本地运行没问题----环境不一致
>
> 2.  多用户相互影响
> 3.  运维成本高
> 4.  解决部署问题

#### 1.2  思想

> 1. 集装箱  ----放置所有内容
> 2. 标准化 ----- 有个码头，所有的集装箱都在码头上；命令的标准化；REST的API，图形化界面。
> 3. 隔离性  ------- 运行时独立开辟空间，互相不影响。
>
> 注册中心 （超级码头）
>
> 镜像  （集装箱）
>
> 容器   （运行起来的镜像）
>
> 

## 二 Docker基本操作

#### 2.1 安装Docker

 ```
   # 1. 下载Docker的依赖环境
   
   yum -y install yum-utils device-mapper-persistent-data lvm2
 ```

   ```
   # 2. 设置下载Docker的镜像⚪
   yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
   ```

   ```
   # 3. 安装Docker
   yum makecache fast
   yum -y install docker-ce
   ```

   ```
   # 4. 启动，设置为开机自动启动， 测试
   systemctl start docker
   systemctl enable docker -- 开机自启
   docker run hello-world
   
   ```

####     2.2 中央仓库

> 1.  国内的镜像网站：网易蜂巢，daoCloud等，下载速度快，但是镜像相对不全。
>
>    https://c.163yun.com/hub#/home 
>
>    http://hub.daocloud.io/ （推荐使用）
>
> 2.  公司内部
>
>    ```
>    #需要创建 /etc/docker/daemon.json，并添加如下内容
>    {
>    	"registry-mirrors":["https://registry.docker-cn.com"],
>    	"insecure-registries":["ip:port"]
>    }
>    #重启两个服务
>    systemctl daemon-reload
>    systemctl restart docker
>    ```
>
>    

#### 2.3 镜像的操作

```
# 拉取 docker pull daocloud.io/library/tomcat:8.0.44-jre8-alpine
# 查看本地镜像 docker images
# 删除镜像  docker  rmi image ID
# 镜像的导入导出  docker save -o 路径 image ID 
# 镜像加载本地镜像 docker load -i 本地包
# 修改镜像名称  docker tag imageID 镜像名：版本
```

#### 2.4 容器的操作

> 1.# 运行容器

```
#简单操作
docker run 镜像的标识|镜像的名称[:tag]
#常用的参数
docker run -d -p 宿主机端口:容器端口 --name 容器名称 镜像的标识|镜像名称[:tag]
#-d:代表后台运行容器
#-p 宿主机端口:容器端口：为了映射当前Linux的端口和容器的端口
#--name 容器名称:指定容器的名称
```

> 2.查看正在运行的容器

```
查看全部正在运行的容器信息
docker ps [-qa]
```

> 3.查看容器日志

```
查看容器日志，以查看容器运行的信息
docker logs -f 容器id

```

> 4.进入容器的内部

```
可以进入容器的内部进行操作
docker exec -it 容器id bash
```

> 5重启&启动&停止&删除容器

```
容器的启动，停止，删除等操作，后续会经常使用到
#重新启动容器
docker restart 容器id
#启动停止运行的容器
docker start 容器id
 
#停止指定的容器(删除容器前，需要先停止容器)
docker stop 容器id
#停止全部容器
docker stop $(docker ps -qa)
#删除指定容器
docker rm 容器id
#删除全部容器
docker rm $(docker ps -qa)
```

