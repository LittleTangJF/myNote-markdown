## 基本数据类型

Number，Boolean，String，bigint, symbol

## 闭包

1. 函数嵌套函数

2. 嵌套的函数可以引用外部变量和参数

3. 因为存在引用，被引用的变量和参数不会被垃圾回收

   ### 闭包用处

   1. **好处**：为了设计私有的**方法和变量**，可以避免**全局变量**的污染，让这些变量始终保持在**内存**中
   2. **缺点**：消耗内存、不正当使用会造成内存溢出的问题

## 原型

简介：当我们需要一个属性的时，`Javascript`引擎会先看当前对象中是否有这个属性，如果没有的就会查找他的`Prototype`对象是否有这个属性，如此递推下去，一直检索到 `Object` 内建对象

### 原型

1. 所有对象中都包含了一个 `[__proto__]` 内部属性
2. 函数对象，除了原型 `[__proto__]` 之外，还预置了 `prototype` 属性。======> 输入fn.prototype====>打开函数对象
3. 函数对象作为构造函数创建实例时，该 prototype 属性值将被作为实例对象的原型 `[__proto__]`。

### 原型链

1. 当一个对象调用的属性/方法自身不存在时，就会去自己 `[__proto__]` 关联的前辈 `prototype` 对象上去找
2. 如果没找到，就会去该 `prototype` 原型 `[__proto__]` 关联的前辈 `prototype` 去找。依次类直到找到属性/方法或 `undefined` 为止。从而形成了所谓的“原型链”

## js事件

1. 事件冒泡：当子元素猝发，会逐级往上传播
2. 事件委托：子元素通过冒泡形势交由父级执行
3. 事件捕获：逐级往下传播j

## jsonp

​		原理：HTML的`script`标签可以加载使用其他域的js,可以动态加载其他域的资源

​		同源策略：必须同<u>**协议、端口、域名**</u>相同，否则跨域

## web storage和Cookie

1. web storage存储5M，Cookie  4K
2. cookie会发送至服务端
3. Cookie设置了有效日期，否则一直生效

## 最简单的继承

```javascript
let  parent = {}
let  child = {}
Object.setPrototypeOf(child,parent);//把parent设置成child的父级
```

## 原型链的理解

## ==和===
#### == 规则

1. String和Number和Boolean和Array ->转换成数字比较
2. 如果类型相同，则比大小
3. null==undefined // true
 ```javascript
[] == ![] //true,左边转换成0，右边先!true->false->0
 ```

## Call和Apply

​		call接受的是展开的数组，apply接受的是数组

## Link和@import

​	link: 发请求，是异步的，主线程还可以继续渲染DOM

​	@import：请求是同步的，所以尽量减少使用，避免阻塞进程

## 深拷贝

　JSON.parse(JSON.stringify(obj))

## instanceof

简介： 检测某个构造函数的prototype属性是否出现在某个实例的原型链上

## document

### 关于网页的3个

1. url: 完整的URL
2. domain: 页面的域名
3. referrer: 保存着链接到当前页面的那个页面的URL