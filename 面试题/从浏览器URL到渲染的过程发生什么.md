## 从浏览器URL到渲染5个过程引发的优化问题

### 1、DNS优化

- 减少解析次数

  ​	方案：DNS缓存

  ​			

- 解析前置

  ​	方案：DNS prefetch

### 2、TCP 优化

- 每次三次握手不得行？

  ​	方案： 长链接、预连接、接入SPDY协议	（前后端共同完成）

### 3、HTPP链接

​	方案：减少请求次数、减少请求体积、借助CDN

#### 	 		资源的压缩与合并（webpack）

​			[webpack-bundle-analyzer](https://www.npmjs.com/package/webpack-bundle-analyzer)分析包大小的工具

​			**Tree-Shaking**：会删除沉余代码，如import

​			**按需加载**：chunk 和 module 的区别：chunk 包含一个或多个 module ，即一个块包含一个或多个模块。

​						vue: 1、vue异步组件技术

​								2、import()

​								3、webpack提供的require.ensure()

​			**gzip**: 服务端确认有Content-Encoding: gzip就可以了，你的浏览器识别出gzip会去解码它的~

​			**图片**：小图标基本都是iconfont以及base64，大图png

​			**CDN**：Content Delivery Network 即分发网络，各地的服务器存有数据的副本，就近原则，前面说的都是缓存，但是**首次连接**得借助CDN

​			     	1、CDN 的核心点有两个，一个是**缓存**，一个是**回源**。**CDN 往往被用来存放静态资源**

### 4、浏览器优化

​	性能优化

​			方案：资源加载优化、服务器渲染、浏览器缓存机制、回流（尺寸）和重绘(背景颜色)

​	**浏览器缓存机制  **  **Response Headers**

​			1、Memory cache

​			2、service worker cache

​			3、http cache

​			4、push cache ( HTTP2 的新特性)

​		**http cache**: **强制缓存**需要服务器设置请求头，**协商缓存**是浏览器自带的

​				**强缓存**

​						Expires 和 Cache-Control控制， 命中时 200 （from disk cache)

​						1、**Expires**: 时间戳

​						2、**Cache-Control**：1、**max-age**（一个相对时间，多少秒内有效）2、**public** 与 **private** 是否能被浏览器缓存 3、**no-store**与**no-cache** 指直接询问服务器，no-store更绝情，不缓存

​				**协商缓存**

​						如果提示not modified 资源会被**重定向**到浏览器缓存 **对应的状态码是 304**

​						1、**last-modified**（时间戳）: 服务器会对比时间戳是否跟最后一次修改一致（不足：不够精确，以秒为单位）

​						2、	**etag**(识别符字符串标识): 	 **Etag 在感知文件变化上比 Last-Modified 更加准确，优先级也更高**			操作： 下一次请求，请求头 **If-None-Match** 会带上etag的标识，服务器与前文件的 hash 值进行比较

​		**memory cache**	

​					Base64 格式的图片，几乎永远可以被塞进 memory cache

## 渲染

### 		告别阻塞：CSS 与 JS 的加载顺序优化

​		CSS 是阻塞渲染的资源。需要将它尽早、尽快地下载到客户端，以便缩短首次渲染的时间。

​		对它使用 **defer** 和 **async** 来避免不必要的阻塞，这里我们就引出了外部 JS 的三种加载方式。

一般当我们的脚本与 DOM 元素和其它脚本之间的**依赖关系不强**时，我们会选用 **async**；当**脚本依赖于 DOM 元素**和其它脚本的执行结果时，我们会选用 **defer**

 **懒加载Lazy-Load **

​			一些图片量比较大的网站（比如电商网站首页，或者团购网站、小游戏首页等）