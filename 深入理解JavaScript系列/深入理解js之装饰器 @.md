## 深入理解js之装饰器 @

1. ### 类装饰器

   - 普通赋予静态方法
   - 高阶传參。@withLanguage('Chinese')

2. ### 类属性装饰器 :@readonly ....

   - 参数s
     - ***target***：被修饰的类
     - ***name***：类成员的名字
     - ***descriptor***：属性描述符，对象会将这个参数传给 `Object.defineProperty`

3. 

   1. 