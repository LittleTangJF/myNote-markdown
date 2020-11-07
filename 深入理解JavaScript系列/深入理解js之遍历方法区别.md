### 深入理解js之遍历方法区别

#### find()

> - 参数(item, index, origin)
> - 返回值（返回符合条件的第一个，否则undefined）

#### findIndex()

> - 参数(item, index, origin)
> - 返回值（返回符合条件的第一个的`位置`，否则-1）

#### filter()

> - 参数(item, index, origin)
> - 返回值（返回符合条件的新数组，否则[]）
> - 特点：**改变原数组的长度，不改变值**

#### forEach()

> - 参数(item, index, origin)
> - 无返回值
> - **无法break**(可try.catch) retrun只能跳出当前会继续循环

#### every()

> - 参数(item, index, origin)
> - 返回值boolean（**全部**符合条件的true，否则false）

#### some()

> - 参数(item, index, origin)
> - 返回值boolean（**只要有一个**符合条件返回true，都不符合false）

#### map()

> - 参数(item, index, origin)
> - 返回值（符合条件的**新数组**，都不符合[]）
> - 特点：**不改变原数组的长度**

#### concat() 数组、字符串混用

> - 参数(arrayStr, arrayStr, ...,arrayStr) 
> - 返回值（**新数组、字符串**）