

## JavaScript常问

- ### 数据类型

  基本数据Number，Boolean，String，bigint, symbol 引用类型Array object

  区别：一个存在栈内存里，引用类型是堆内存里 **详细说说**

- ### 闭包

  - 函数嵌套函数

  - 嵌套的函数可以引用外部变量和参数

  - 因为存在引用，被引用的变量和参数不会被垃圾回收

  ### 闭包用处

  1. **好处**：为了设计私有的**方法和变量**，可以避免**全局变量**的污染，让这些变量始终保持在**内存**中
  2. **缺点**：消耗内存、不正当使用会造成内存溢出的问题

- ### 原型与原型链

  原型链简介：当我们需要一个属性的时，`Javascript`引擎会先看当前对象中是否有这个属性，如果没有的就会查找他的`Prototype`对象是否有这个属性，如此递推下去，一直检索到 `Object` 内建对象

- ### 原型


1. 所有对象中都包含了一个 `[__proto__]` 内部属性
2. 函数对象，除了原型 `[__proto__]` 之外，还预置了 `prototype` 属性。======> 输入fn.prototype====>打开函数对象
3. 函数对象作为构造函数创建实例时，该 prototype 属性值将被作为实例对象的原型 `[__proto__]`。

- ### 原型链


1. 当一个对象调用的属性/方法自身不存在时，就会去自己 `[__proto__]` 关联的前辈 `prototype` 对象上去找
2. 如果没找到，就会去该 `prototype` 原型 `[__proto__]` 关联的前辈 `prototype` 去找。依次类直到找到属性/方法或 `undefined` 为止。从而形成了所谓的“原型链”

- ### js事件机制

  - 事件冒泡：当子元素猝发，会逐级往上传播
  - 事件委托：子元素通过冒泡形势交由父级执行
  - 事件捕获：逐级往下传播j

- ### 跨域


​		原理：HTML的`script`标签可以加载使用其他域的js,可以动态加载其他域的资源

​		同源策略：必须同<u>**协议、端口、域名**</u>相同，否则跨域

- ### web storage和Cookie

  - web storage存储5M，Cookie  4K

  - cookie会发送至服务端

  - Cookie设置了有效日期，否则一直生效

    起源：**HTTP 是无状态的协议**维护状态通过 cookie 或者 session 去实现

    **为什么不推荐放token在cookie？**

    ​		cookie在浏览器发送请求的时候会被自动带上

    ​		CSRF跨站请求伪造，防止这个攻击

    ​				1、cookie：用户点击了链接，cookie未失效，导致发起请求后后端以为是用户正常操作，于是进行扣款操作；

    ​				2、token：用户点击链接，由于浏览器不会自动带上token，所以即使发了请求，后端的token验证不会通过，所以不会进行扣款操作

    **如何设置cookie？**

    ​		document.cookie = key "=" value "; " expires; ------- string

- ### 寄生组合的继承

  - call去执行父类 Parent.call(student, arg)

  - 子类实例的原型prototype等于父类的实例new Parent

    解析：在 stu1 = new Student() 构造函数时，Student 内部 this 的值指向的是 stu1, 所以 **this**.stuID =**stu1**.stuID, 所以 Person.call(**this**, name, age) 就相当于Person.call(**stu1**, '王宝宝', 20)，就相当于 stu1.Person('王宝宝',20)。最后，stu1 去调用 Person 方法时，Person 内部的 this 指向就指向了 stu1。那么Person 内部this 上的所有属性和方法，都被拷贝到了stu1上。说到这里，大家应该清楚一点点了吧。

    https://www.cnblogs.com/ranyonsue/p/11201730.html

- ### 如何把es6的class转换为es5的类

- ### Call和Apply


​		call接受的是展开的数组，apply接受的是数组

- ### Link和@import


​	link: 发请求，是异步的，主线程还可以继续渲染DOM

​	@import：请求是同步的，所以尽量减少使用，避免阻塞进程

- ### 深浅拷贝

  　区别1: 元素只有值，没有引用，那浅拷贝和深拷贝没有差别，都会将原有对象复制一份，产生一个新对象，对新对象里的值进行修改不会影响原有对象，新对象和原对象完全分离开。

     区别2: 深拷贝则不同，它会将原对象里的引用也新创建一个，即新建一个列表，然后放的是新列表的引用，这样就可以将新对象和原对象完全分离开。

- ### 实现instanceof

  简介： 检测某个构造函数的prototype属性是否出现在某个实例的原型链上

- ### document

  ### 关于网页的3个

  - url: 完整的URL
  - domain: 页面的域名
  - referrer: 保存着链接到当前页面的那个页面的URL

## ES6

[地址](https://blog.csdn.net/m0_37686205/article/details/88776259?utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control)

1. **箭头函数**

   作用：

   1. 类似于匿名函数，在某些情况下使用，可减少代码量
   2. 箭头函数没有`prototype`(原型)，所以箭头函数本身没有`this`
   3. 箭头函数的`this`指向在定义的时候继承自外层第一个普通函数的this
   4. 箭头函数不支持`new.target`
   5. 无**箭头函数的`this`指向全局，使用`arguments`会报未声明的错误**，如果指向普通函数就是他的arguments ---可用...rest来获取不定量的参数
   6. **箭头函数不支持重命名函数参数,普通函数的函数参数支持重命名**
   7. 不支持的场景
      1. 在对象内访问内部的属性
      2. 动态回调，如addEventListener，需要用普通函数，不然会之乡window

2. 模板字符串---用反引号（`）标识

3. 解构赋值 

4. for of循环for...of循环可以遍历数组、

   1. for in 一般常用来遍历对象
   2. for of数组对象都可以遍历，遍历对象需要通过和Object.keys()
   3. for in循环出的是key，for of循环出的是value

5. Set和Map结构

6. import、export导入导出

7. ... 展开运算符

8. 修饰器 @decorator是一个函数，用来修改类甚至于是方法的行为。

9. class 类

10. Promise是异步编程的一种解决方案--优势；Promise的优势在于，可以在then方法中继续写Promise对象并返回，然后继续调用then来进行回调操作。

    1. 简介： Promise构造函数，传入两个参数：**resolve，reject**，resolve是将Promise的状态置为**fullfiled**，reject是将Promise的状态置为**rejected**

    2. 初始状态是 `pending`，能够转换成 `fulfilled` 或 `rejected` 状态。

    3. ```js
       // 优雅使用Promise，建一个匿名函数，1\return new Promise 2\链式调用
       function getUserInfo () {
           return getData().then(
               data => {
                   return data
               }
           )
       }
       ```

       

    4. Promise构造函数是同步执行的，then方法是异步执行的

    5. 与async、await的区别
       1. promise是ES6，async/await是ES7，且都是非阻塞
       2. async/await使得异步代码看起来像同步代码
       3. promise错误可以通过catch来捕捉，async/await既可以用.then又可以用try-catch捕捉

11. Symbol是一种基本类型

12. Proxy代理