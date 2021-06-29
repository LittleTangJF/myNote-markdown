## CSS常见面试题

- #### 块、行级元素

  - 块(block)：**div,H1-6,ul,li,p,dl,dt,table,form**
    - 可以设置w|h|padding|margin

  - 行(inline)：**a, i, b, span, label** (input, img)
    - h|line-h|底边距border-bottom-width固定不可设置
  - 行内块状元素(inline-block):**img 和input**
    - vertical-align: middle;可以居中
    - 可以设置w|h|padding|margin

- **BFC  Block Formatting Contexts块级格式化上下文**

  - 特点
    - 独立容器
    - 独特的特性
      - 容器下margin上下边距重叠
      - 包含浮动元素-清除浮动
      - 避免被浮动元素覆盖
  - 触发
    -  根元素
    - 浮动元素：float 除 none 以外的值
    - 绝对定位元素：position (absolute、fixed)
    - display 为 inline-block、table-cells、flex
    - overflow 除了 visible 以外的值 (hidden、auto、scroll)

- **css样式隔离**

  - 严格的命名规范（不能完全避免）
  - CSS Modules
    - import引入使用类名属性，然后打包会自动将类名转换成 hash 值
    - 打包：配置css-loader打包加上hash值
  - CSS In JS
    - react中使用的styled-components：就是将css用js的方式写

- #### 清除浮动原理[视频](https://www.bilibili.com/video/BV1h54y1D7rb?from=search&seid=17512387739467067458)

  - 原理：当容器高度auto,其内容有浮动的元素，这样容器就不会自动伸长适应。
  - 解决方法：overflow、clearboth、定义height
    - 1.父级定义高度height
    - 2.容器内最后添加一个div:clear:both
    - position: absolute/fixed
    - float: 不为none
    - overflow: 不是visible(不设置浮动元素会溢出)
    - display: inline-block(解决外边距塌陷)/flex
  
- #### 居中显示

  - 绝对定位

    ```css
    方法1
    position: absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%)
    方法2
    上下左右：0；
    margin:auto;
    ```

  - 弹性盒flex

    ```css
    display:flex;
    justify-content:center;
    align-items:center;
    ```

- #### 盒模型 

  ​	切换模型：box-sizing:content-box/border-box; 默认content-box

  - W3C标准盒模型：width==content
  - IE盒模型：width==content + padding + border

- #### 选择器和权重问题 [详细地址](https://www.cnblogs.com/Tony100/p/10038860.html)

  -  选择器：ID、class、伪类:hover、属性选择器[title]、tag标签、通配符*、伪元素::before、相邻选择器+、子选择器>
  - 权重：

  1. 第一等：内联样式 style=‘’     1000
  2. 第二等：ID                            100
  3. 第三等：==class==类/伪类:hover/属性选择器[title]        10
  4. 第四等：标签tag/伪元素           1



![权重实例](http://www.nowamagic.net/csszone/images/priority_rules_2.jpg)



- #### 三栏布局

  - float : 左右浮动
  - flex：左右给固定width,中间flex:1自由撑开
  - position：全部使用绝对定位

- ### 讲一下position的取值和他们的作用，讲一下absolute相对谁定位，那么relative, fixed呢


1. - position： static默认、absolute绝对定位、relative相对定位、fixed固定定位、inherit继承父元素

   1. absolute： 相对于夫元素
   2. relative：相对于自身定位 left：-10左移动10
   3. fixed：相对窗口

- ### 这三个定位如果相互堆叠的话，显示的顺序是怎样的，层级

  解答：*属于同一个层叠上下文，此时谁的z-index值大，谁在上面*

  层级显示规则

  *规则：从后到前*

​    *1、设置了border/background==>  html根元素

​    *2、设置了z-index为负值*

​    *3、常规的块级元素（非定位*

​    *4、设置了浮动元素*

​    *5、常规的行级元素（非定位*

​    *6、设置了z-index：auto的定位元素*

​    *7、设置了z-index：正整数的定位元素*

<img src='https://segmentfault.com/img/remote/1460000021571287' style='zoom:0.7'/>

- ### 6、如果有用到transform、translate，它们的层级是怎样的

  css3元素对层级上下文的影响，**子元素就无法穿透父元素**

  ​		1、父级是 `display: flex` 或者 `display: inline-flex;`

  ​		2、如果元素的 `opacity` 不为1，这个元素为层叠上下文元素

  ​		3、应用了 `transform` 的元素为层叠上下文元素

  ​		4、具有 `filter` 属性的元素是层叠上下文元素

