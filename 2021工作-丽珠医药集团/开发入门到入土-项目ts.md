## 啊鹿诊所PC项目

1. React.CSSProperties： react基于typescript 定义的css的属性类，这里其实就是规定了 divStyle这个函数 返回的类型 是CSSProperties

2. **引入classnames库**：由于react原生动态添加多个className会报错

3. grid布局：Grid 布局只对项目生效。

   1. grid-template-rows: 行高，可用100px或者百分比

      1.  **repeat(3, 33.33%)**
      2. **auto-fill**  自动填充
      3. **fr**  倍数
      4. **minmax**  它接受两个参数，分别为最小值和最大值
      5. **auto** 关键字表示由浏览器自己决定长度。

   2. grid-template-columns

   3. grid-row-gap、grid-column-gap 间距

   4. ## 项目属性

      1. ### grid-column-start: 2;  左边框是第二根垂直网格线 

      2. grid-column-end: 4; 右边框是第四根垂直网格线。

      3. grid-row-start: 2;

      4. grid-row-end: 4;

      5. grid-column-start: span 2; 1号项目的左边框距离右边框跨越2个网格。

4. typescript

   1.  `Omit<T, K>` 帮助类型
      1. 解析：帮助我们从另一个对象中剔除某些属性，并创建一个新的对象类型
   2.  Partial
       1.  解析：可以快速把某个接口类型中定义的属性变成可选的(Optional)
   3.  使用泛型
   4.  方法的重载
   5.  Pick就是从一个复合类型中，取出几个想要的类型的组合
   
5. class

   1. class 中get 和set的用法
      解析：如果你要对name进行一些操作的话 可以使用 get 和 set 来进行操作
   2. readonly 的用法
      1. 解析：// 会提示 该属性是不可以修改的
   3. 使用static的方法
      1. class的静态属性和静态方法定义在类上，实例不会继承静态属性和静态方法
   4. useRef
      1. 这个hooks函数，除了传统的用法之外，它还可以“跨渲染周期”保存数据，修改state会引起组件重新渲染
   
6. events

   1. 引入 **import** { EventEmitter } **from** 'events'
   2. 实例化 **export** **default** **new** EventEmitter()
   3. 实例emitter 设置最大监听数量 emitter.setMaxListeners(10)
   4. 