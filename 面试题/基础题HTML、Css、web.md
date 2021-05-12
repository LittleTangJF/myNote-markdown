## Cookies

起源：**HTTP 是无状态的协议**维护状态通过 cookie 或者 session 去实现

**为什么不推荐放token在cookie？**

​		cookie在浏览器发送请求的时候会被自动带上

​		CSRF跨站请求伪造，防止这个攻击

​				1、cookie：用户点击了链接，cookie未失效，导致发起请求后后端以为是用户正常操作，于是进行扣款操作；

​				2、token：用户点击链接，由于浏览器不会自动带上token，所以即使发了请求，后端的token验证不会通过，所以不会进行扣款操作

**如何设置cookie？**

​		document.cookie = key "=" value "; " expires; ------- string

## SEO

- 合理的title`、`description`、`keywords
- 语义化的`HTML`代码



## 从浏览器地址栏输入url到显示页面的步骤

### 基础版

1、浏览器根据请求的`URL`交给`DNS`域名解析，找到真实`IP`，向服务器发起请求

2、服务器交给后台处理完成后返回数据，浏览器接收文件（`HTML、JS、CSS`、图象等）；

3、浏览器对加载到的资源（`HTML、JS、CSS`等）进行语法解析，建立相应的内部数据结构（如`HTML`的`DOM`）；

4、载入解析到的资源文件，渲染页面，完成

### 详细版

1. 输入url————
2. 浏览器查看缓存
   1. no——请求
   2. yes ——检查新鲜-两个HTTP头
      1. Expires: 值为一个绝对时间表示缓存新鲜日期
      2. Cache-Control：max-age=,值为以秒为单位的最大新鲜时间
3. 浏览器**解析URL**获取协议，主机，端口，path
4. 浏览器**组装一个HTTP（GET）请求报文**
5. 浏览器**获取主机ip地址**
   1. 浏览器缓存
   2. 本机缓存
   3. hosts文件
   4. 路由器缓存
   5. ISP DNS缓存
   6. DNS递归查询
6. **打开一个socket与目标IP地址，端口建立TCP链接**
   1. 客户端发送一个TCP的**SYN=1，Seq=X**的包到服务器端口
   2. 服务器发回**SYN=1， ACK=X+1， Seq=Y**的响应包
   3. 客户端发送**ACK=Y+1， Seq=Z**
7. TCP链接建立后**发送HTTP请求**
8. 服务器将**响应报文通过TCP连接发送回浏览器**
9. 浏览器接收HTTP响应，然后根据情况选择**关闭TCP连接或者保留重用，关闭TCP连接的四次握手如下**：
   1. 主动方发送**Fin=1， Ack=Z， Seq= X**报文
   2. 被动方发送**ACK=X+1， Seq=Z**报文
   3. 被动方发送**Fin=1， ACK=X， Seq=Y**报文
   4. 主动方发送**ACK=Y， Seq=X**报文
10. **解析HTML文档，构件DOM树，下载资源，构造CSSOM树，执行js脚本**，这些操作没有严格的先后顺序，以下分别解释

## 你有做过什么前端优化吗



首先考虑四个要点1、加载资源优化 2、 渲染优化 3、浏览器缓存策略 4、图片优化

​	到我们输入**当我们输入URL时，我们要知道这中间发生了什么**？

​	我们可以优化的点

​	1、**合理的设置http缓存**

​	2、**资源合并与压缩**

​	3、**浏览器缓存**

​	4、**图片优化**--大小和格式

​	5、**节流和防抖**

​	6、减少 Cookie 的大小

1、文件压缩`Gzip`压缩

2、使用`CDN`（将源站分发到用户附近站点）

3、减少`HTTP`请求

4、减少`DNS`查询 

5、减少dom节点，减少DOM操作次数 innerHTML

6、减小`cookie`大小

7、添加Expires头，服务端配置Etag

8、前端自动化（gulp/webpack）

9、css： `link`最大限度支持并行下载，`@import`过多嵌套导致串行下载

10、避免使用CSS动态属性

11、图片懒加载。 异步加载

12、减少重绘和回流

​	

## **浏览器内核**

1、`Trident`内核：IE、360

2、`Webkit`内核：Safari,Chrome

3、`Firefox`：`gecko`内核

## html5有哪些新特性

1、新增选择器（document.querySelector`、`document.querySelectorAll）

2、媒体播放、video` 和 `audio

3、localStorage` 和 `sessionStorage

4、语意化标签 article`、`footer`、`header`、`nav`、`section

5、增强表单控件Form=> calendar`、`date`、`time`、`email`、`url`、`search

6、`Form Data` 对象

7、全双工通信协议 `websocket`

8、绘画 `canvas`

##  存储

1、cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递

2、`sessionStorage`和`localStorage`不会自动把数据发给服务器，仅在本地保存

存储大小：

1、`cookie`数据大小不能超过4k

2、`sessionStorage`和`localStorage`虽然也有存储大小的限制，但比`cookie`大得多，可以达到5M或更大

有期时间：

1、`localStorage` 存储持久数据，浏览器关闭后数据不丢失除非主动删除数据

2、`sessionStorage` 数据在当前浏览器窗口关闭后自动删除

3、`cookie` 设置的`cookie`过期时间之前一直有效，即使窗口或浏览器关闭

## 行内元素有哪些？块级元素

1、行内元素有：`a b span img input select strong`

2、块级元素有：`div ul ol li dl dt dd h1 h2 h3 h4… p`

3、空元素：`<br> <hr> <img> <input> <link> <meta>`

## git fetch和git pull的区别

1、`git pull`：相当于是从远程获取最新版本并`merge`到本地

2、git fetch`：相当于是从远程获取最新版本到本地，不会自动`merge