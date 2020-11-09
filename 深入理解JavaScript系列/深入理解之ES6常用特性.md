#### 1.变量声明关键字let、const

#### 2. 函数拓展-----function

- ###### 参数设置默认值

- ###### 箭头函数

- ###### async函数

#### 3.三点运算符(...)

#### 4.class类

#### 5.解构赋值

> ```js
> let {a, b, ...rest} = {a: 10, b: 20, c: 30, d: 40};//rest = {c: 30, d: 40}
> ```

#### 6.for...of

#### 7.字符串模板 ``

#### 8.Promise对象

#### 9.Generator函数（umijs)

#### 10.字符串拓展

- includes(str) : 判断是否包含指定的字符串
- startsWith(str) : 判断是否以指定字符串开头
- endsWith(str) : 判断是否以指定字符串结尾
- repeat(count) : 重复指定次数

#### 11.Array拓展

- findIndex(function(value, index, arr){return true}) : 找出第一个满足条件返回true的元素下标
- find(function(value, index, arr){return true}) : 找出第一个满足条件返回true的元素

#### 12.对象拓展

- Object.assign(target, source1, source2..)：将源对象的属性复制到目标对象上