### 一、安全访问对象

#### 1.数组问题

- 非空判断，数组判断Array.isArray()

```js
const {code, msg, data} = await fetchList()
data.forEach(()=>{}) // 可能会出现err
Array.isArray(data) && data.forEach(()=>{})// 判断
```

#### 2.空值判断

- 对象某个属性时如`x.y.z`，最好检测一下`x`和`y`是否存在

```js
let z = x && x.y && x.y.z  // 麻烦
let z = a?.y?.z;  // 2020新的?.语法
```

3.

### 二、错误异常处理

#### 1.通过throw语句抛出一个自定义错误对象