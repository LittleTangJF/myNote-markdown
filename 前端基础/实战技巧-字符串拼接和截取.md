> Object.keys()和subString()
>
> Object.keys():返回(对象中可直接枚举的属性)的一个所有元素为字符串的**数组**
```javascript
arr={key:value}
Object.keys(arr).forEach((key)=>{
    query+= `${key}=${arr[key]}&`
})
querys= query.subString(0,query.length-1) //去除最后一个&
```

> - 掘金

掘金