# Mysql

## 开始

1. ### pull

   - docker pull mysql:latest /  docker pull mysql/mysql-server

2. ### start

   - docker run -itd --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql/mysql-server

3. ### password

   - docker logs mysql

4. ### exec：进入容器

   - docker exec -it mysql bash

5. -uroot: 进入mysql

   1. mysql -uroot -p       
   2. 输入password

6. create远程用户

   - ALTER USER 'root'@'localhost' IDENTIFIED BY 'tjf123';
   - CREATE USER 'tangjf'@'%' IDENTIFIED WITH mysql_native_password BY 'tjf123';
   - GRANT ALL PRIVILEGES ON *.* TO 'tangjf'@'%';

7. 

   - 

- 

1. ### 

- d

  

## 连接方式

1. tcp/ip(传输控制协议/网际协议): `MySQL`采用`TCP`作为服务器和客户端之间的网络通信协议

   >TCP/IP协议是Internet最基本的协议,其中应用层的主要协议有[Telnet](https://baike.baidu.com/item/Telnet/810597)、[FTP](https://baike.baidu.com/item/FTP/13839)、[SMTP](https://baike.baidu.com/item/SMTP/175887)等，是用来接收来自传输层的数据或者按不同应用要求与方式将数据传输至传输层；运输层的主要协议有[UDP](https://baike.baidu.com/item/UDP/571511)、TCP，是使用者使用平台和计算机信息网内部数据结合的通道，可以实现数据传输与数据共享；网络层的主要协议有ICMP、IP、IGMP，主要负责网络中数据包的传送等；而网络访问层，也叫网路接口层或数据链路层，主要协议有ARP、[RARP](https://baike.baidu.com/item/RARP/610685)，主要功能是提供链路管理错误检测、对不同通信媒介有关信息细节问题进行有效处理等。 [3]

   OSI模型共有七层，别是物理层、数据链路层、网络层、运输层、会话层、表示层和应用层

   1. 应用层、表示层、会话层 ===> 应用层 ：应用进程提供服务

   2. 运输层

   3. 网络层

   4. 数据链路层和物理层====> 网络接口层

      <img src='https://bkimg.cdn.bcebos.com/pic/3bf33a87e950352ad2fb2dca5d43fbf2b3118b5d?x-bce-process=image/resize,m_lfit,w_640,limit_1/format,f_auto'/>

## 查询过程-解析优化

1. 查询缓存

   `INSERT`、 `UPDATE`、`DELETE`、`TRUNCATE TABLE`、`ALTER TABLE`、`DROP TABLE`或 `DROP DATABASE`语句，那使用该表的所有高速缓存查询都将变为无效并从高速缓存中删除！

1. 语法解析

   `MySQL`服务器程序首先要对这段文本做分析，判断请求的语法是否正确

2. 查询优化

   外连接转换为内连接、表达式简化、子查询转为连接

## 查询过程-存储引擎

人们把`连接管理`、`查询缓存`、`语法解析`、`查询优化`这些并不涉及真实数据存储的功能划分为`MySQL server`的功能，把真实存取数据的功能划分为`存储引擎`的功能。

`MySQL`提供了各式各样的`存储引擎`，不同`存储引擎`管理的表具体的存储结构可能不同，采用的存取算法也可能不同。

1. >常用存储引擎

   ​	<img src='https://img2018.cnblogs.com/blog/423756/201810/423756-20181031083442773-1716650217.png' style="zoom:0.6" />





