## 索引类型

#### 		索引类型查询操作符 ( keyof )

索引访问操作符 ( T[K] )

### 		例子

​		实现一个 ts 的工具函数 `GetOnlyFnProps<T>` 

- ​		

  ```tsx
  type GetOnlyFnKeys<T extends object> = { // T是对象
    
    //Key in keyof T 指key是对象的ke y
    //T[K] 是对象的所有key
    //相当于排除掉了值类型不是 function 的，并且现在新的值是 K
   	[Key in keyof T]: T[K] extends Function ? K : never
  }
  type GetOnlyFnProps<T extends object> = {
      [K in GetOnlyFnKeys<T>]: T[K]
  }
  测试
  type ccc = GetOnlyFnProps<obj>
  
  let value:ccc = {
      a: () => '1'
  }
  ```

  



