

#### 基本类型 7种 boolean undefined null number string **symbol** **bigint**

>**bigint** 比number支持更大的数值，数值溢出将不是问题+2^51-1
>**symbol** 唯一的标识符
#### 引用类型 Object( Array Function RegExp Date Math )

>null不是对象，000开头表示对象但是null的地址表示全为0，对于基础类型typeOf除了null都是正确类型，但typeOf对于引用类型，除了函数外都是Object

#### JavaScript兼容性检测 [地址](https://caniuse.com)
#### 常用API
> filter():生成新的数组，筛选出所需要的
```javascript
let arr = ARR.filter((value)=>{
    return value==3;
})
```
>indexOf: 返回字符串首次出现的位置，没有则返回-1

>splice(index, howmany): index从哪开始，howmany删除的数量

>slice(start, end): start开始的位置， end结束的位置（不包含）


>replace(reg, target) :常用来做正则替换

```javascript
str = str.replace(/\[(.+?)\]/, `<img src="$1"/>`);//每个括号代表分组，$0~$9 分组
```

#### 常用的方法

>**递归**: 它不像for循环一样，每执行一次即返回结果，递归是先‘递’到底了，再‘归’返回**整个调用栈**的执行结果。

>函数参数Function(arguments): 函数传递对象参数是该对象在堆中的内存地址

