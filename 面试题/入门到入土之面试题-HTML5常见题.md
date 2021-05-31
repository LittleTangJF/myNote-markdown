## HTML5常见面试题

- ### 浏览器内核

  1、`Trident`内核：IE、360

  2、`Webkit`内核：Safari,Chrome

  3、`Firefox`：`gecko`内核

- ### html5有哪些新特性

  1、新增选择器（document.querySelector`、`document.querySelectorAll）

  2、媒体播放、video` 和 `audio

  3、localStorage` 和 `sessionStorage

  4、语意化标签 article`、`footer`、`header`、`nav`、`section

  5、增强表单控件Form=> calendar`、`date`、`time`、`email`、`url`、`search

  6、`Form Data` 对象

  7、全双工通信协议 `websocket`

  8、绘画 `canvas`

- ###  存储

  1、cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递

  2、`sessionStorage`和`localStorage`不会自动把数据发给服务器，仅在本地保存

  存储大小：

  1、`cookie`数据大小不能超过4k

  2、`sessionStorage`和`localStorage`虽然也有存储大小的限制，但比`cookie`大得多，可以达到5M或更大

  有期时间：

  1、`localStorage` 存储持久数据，浏览器关闭后数据不丢失除非主动删除数据

  2、`sessionStorage` 数据在当前浏览器窗口关闭后自动删除

  3、`cookie` 设置的`cookie`过期时间之前一直有效，即使窗口或浏览器关闭

- ### 行内元素有哪些？块级元素

  1、行内元素有：`a b span img input select strong`

  2、块级元素有：`div ul ol li dl dt dd h1 h2 h3 h4… p`

  3、空元素：`<br> <hr> <img> <input> <link> <meta>`