### 、深入理解js之遍历方法区别

#### find()

1. 参数(item, index, origin)
2. 返回值（返回符合条件的第一个，否则undefined）



#### findIndex()

1. 参数(item, index, origin)
2. 返回值（返回符合条件的第一个的`位置`，否则-1）

#### filter()

1. 参数(item, index, origin)
2. 返回值（返回符合条件的新数组，否则[]）
3. 特点：**改变原数组的长度，不改变值**

#### forEach()

1. 参数(item, index, origin)
2. 无返回值
3. **无法break**(可try.catch) retrun只能跳出当前会继续循环

#### every()

1. 参数(item, index, origin)
2. 返回值boolean（**全部**符合条件的true，否则false）

#### some()

1. 参数(item, index, origin)
2. 返回值boolean（**只要有一个**符合条件返回true，都不符合false）

#### map()

1. 参数(item, index, origin)
2. 返回值（符合条件的**新数组**，都不符合[]）
3. 特点：**不改变原数组的长度**

#### concat() 数组、字符串混用

1. 参数(arrayStr, arrayStr, ...,arrayStr) 
2. 返回值（**新数组、字符串**）

#### for  in (适合对象)-key

1. 特点：*for in遍历的是数组的索引（即键名）index
2. 会遍历所有的可枚举属性，包括原型上的key
3. 上条会出现当有原型上的key也会遍历出来，所以可以用for...of + Object.keys() 代替

#### for  of (不能用于对象)-value

1. 特点：没有部署原生的 iterator 接口，直接使用 for...of 会报错（不能对对象用）