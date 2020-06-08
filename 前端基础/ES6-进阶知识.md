### 学习地址
[学习地址](https://muyiy.cn/blog/3/3.2.html)

#### 1. 函数>变量（优先级）

#### 2.1 栈数据结构（先进后出）
![bcc45a26fb46f1905e34903b2d6d973a.jpeg](en-resource://database/570:1)@w=400

#### 2.2 队列（先进先出）
![f2f79f7794cfccd6cab7db6d732b6040.jpeg](en-resource://database/571:1)@w=500

#### 2.3类型存储
![9dfe524398c727f40839091a2c03ca4e.png](en-resource://database/572:1)
例子：改变a的类型，不会影响b的引用类型的值，所以b还是{ name: '前端开发' }

```javascript
var a = { name: '前端开发' }var b = a;
a = null;
```
#### 2.4 内存空间管理（垃圾回收）
>局部变量在函数执行完后会被标记垃圾回收，但是全局变量不会，所以避免使用全局变量

垃圾回收通常采用引用计数法：就是看一个对象是否用指向他的引用，如没有其他对象指定他了，就会清除。如果两个对象相互引用，则会造成**内存泄露**

#### 3. const声明的对象
> const 声明对象时，保存的仅仅只指向栈的**指针**的保存，const只能保证指向栈的指针是固定的（总是指向一个固定的地址），至于他指向的数据结构是否可变就不能控制了

#### 4. 闭包（题）
 （1）以减少全局变量的使用。从而使用闭包模块化代码，减少全局变量的污染。    （优点）
   (2）常驻内存会增大内存使用量，并且使用不当很容易造成内存泄露。（缺点）

产生的条件是：当前作用域存在对父级作用域的引用
>for循环后所有全局的执行上下文OV是i=3;解决方法：var=>let 或者data[i]赋值(func)(i)
```javascript
 var data = [];
 for(var i = 0;i<3;i++){
    data[i] = function(){
    console.log(i) // 3 3 3
 }
 }
```
#### 5. this绑定解析
this的绑定规则有以下5种
1. 默认绑定 undefined
2. 隐式绑定 :存在上下文对象（在对象中）this就是当前对象 ;var fuc= obj.func会丢失，同理，func当初参数传递会丢失
3. 显式绑定 :通过call()和apply()方法
4. new绑定 :使用new创建新对象时，会绑定到函数调用的this
5. 箭头函数绑定

##### 实例化
解释：通常需要一个模板，表示某一类事物的特征，然后根据这个类生成，这个过程就叫做实例化
应用：通常静态的成员变量是可以直接引用的，而非静态的成员变量则需要实例化才可以使用
特点：（1）new会改变this指向，指向实例化的实例


>手写new

```javascript
function create(){
    var obj = new Object();// 创建空对象，返回
    Con = [].shift.call(arguments) // 取出第一个参数-构造函数
    obj._proto_ = Con.prototype; // obj对象指向构造函数的原型，obj可访问它的原型属性
    var ret = Con.apply(obj,arguments);// Con 继承了obj的属性，可以访问obj的属性
    return ret instanceOf Object? ret : obj;
}
```
>apply: 劫持另外一个对象的方法，继承另外一个对象的属性，总是使用null来忽略this绑定可能参数的副作用
#### 6. 深浅拷贝原理
>基本类型的赋值不会影响另一个，地址不同
>引用类型的两个赋值是指向通一个地址，改变a会影响b
##### 6.1 浅拷贝 slice() concat() assign()
##### 6.2 深拷贝  JSON.parse(JSON.stringify(object))
弊端：1. 内存在深层的对象无法拷贝 2. new Date()不行 3. 内含正则不行 4 undefined、symbol、function直接忽略
>实现一个深拷贝

```javascript
function deepcopy(obj){
    if (!isObject(source)) return source; // null返回false 如果是对象和数组都返回true
    var target = obj.isArray?[]:{}; //看是数组还是对象
    for(var key in obj){
    if(Object.prototype.hasOwnPrototype.call(obj,key){ // 判断对象obj是否有key属性
        if( typeOf obj[key]===‘Object’){ 
         target[key] = deepcopy(obj[key]) // 递归
         }else{
         target[key]= obj[key]
          }
        }
     return target;
}

```
#### 7. 原型prototype
javascript 是一种基于原型的语言

#### 8. 高阶函数
1. 接受一个或多个函数作为参数输入
2. 输出一个函数

##### 柯里化
>函数柯里化又称部分求值，柯里化是一种将多个参数的函数转换为一系列使用一个参数的函数，并且返回接受余下的参数而且返回结果的新函数的技术