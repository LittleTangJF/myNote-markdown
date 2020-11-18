#### 1.增加json对象

- JSON.stringify(obj/arr);
- JSON.parse(json);

#### 2.拓展了数组方法

> ```js
> Array.isArray()            方法检查对象是否为数组
> Array.forEach(funName)     每个数组元素调用一次函数
> Array.map(funName)         遍历数组返回一个新数组，返回加工后的值
> Array.filter(funName)      遍历过滤出一个新的子数组，返回条件为true的值
> Array.reduce(funName)      按funName方法处理数组，最后返回一个值，funName有两个参数，第一个是最后返回的归并值，第二个是元素
> Array.reduceRight(funName) 同上，只是从最后一个数据开始计算
> Array.every(funName)       遍历数组，检查是否每一个值都符合条件，返回bool    
> Array.some(funName)        遍历数组，检查是存在至少一个值符合条件，返回bool
> Array.indexOf(value)       检索数组中的某个元素值并返回其位置,多个则返回第一个
> Array.lastIndexOf(value)   同上，只是从最后开始检索
> ```

#### 3.对象属性增加getter\setter

#### 4.函数----function

> - Function.prototype.bind(obj)
> - **bind()与call()和apply()的区别**
>   -   call:   ...params
>   - apply:  params[]

