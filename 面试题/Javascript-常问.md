### 基本数据类型

Number，Boolean，String，bigint, symbol

### 闭包

     		1. 函数嵌套函数
     		2. 嵌套的函数可以引用外部变量和参数
     		3. 因为存在引用，被引用的变量和参数不会被垃圾回收

### js事件

1. 事件冒泡：当子元素猝发，会逐级往上传播
2. 事件委托：子元素通过冒泡形势交由父级执行
3. 事件捕获：逐级往下传播j

### jsonp

​		原理：HTML的`script`标签可以加载使用其他域的js,可以动态加载其他域的资源

​		同源策略：必须同<u>**协议、端口、域名**</u>相同，否则跨域

### web storage和Cookie

1. web storage存储5M，Cookie  4K
2. cookie会发送至服务端
3. Cookie设置了有效日期，否则一直生效

### 最简单的继承

```javascript
let  parent = {}
let  child = {}
Object.setPrototypeOf(child,parent);//把parent设置成child的父级
```

### 原型链的理解

#### ==和===
>== 规则
1. String和Number和Boolean和Array ->转换成数字比较
2. 如果类型相同，则比大小
3. null==undefined // true
 ```javascript
[] == ![] //true,左边转换成0，右边先!true->false->0
 ```

### Call和Apply

​		call接受的是展开的数组，apply接受的是数组

### Link和@import

​	link: 发请求，是异步的，主线程还可以继续渲染DOM

​	@import：请求是同步的，所以尽量减少使用，避免阻塞进程

### 深拷贝

　JSON.parse(JSON.stringify(obj))