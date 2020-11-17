#### 块、行级元素

- 块(block)：**div,H1-6,ul,li,p,dl,dt,table,form**
  - 可以设置w|h|padding|margin

- 行(inline)：**a, i, b, span, label** (input, img)
  - h|line-h|底边距border-bottom-width固定不可设置
- 行内块状元素(inline-block):**img 和input**
  - vertical-align: middle;可以居中
  - 可以设置w|h|padding|margin

#### 清除浮动原理

- 原理：当容器高度auto,其内容有浮动的元素，这样容器就不会自动伸长适应。
- 解决方法：overflow、clearboth、定义height
  - 1.父级定义高度height
  - 2.容器内最后添加一个div:clear:both
  - 3.给容器加overflow：hidden
#### 居中显示

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
#### 盒模型 

​	切换模型：box-sizing:content-box/border-box;

- 标准盒模型：width==content
- IE盒模型：width==content + padding + border
#### 选择器和权重问题 [详细地址](https://www.cnblogs.com/Tony100/p/10038860.html)

	1. ID #id
 	2. class .class
 	3. 标签 tag
 	4. 通用/通配符 *
 	5. 伪类 :hover
 	6. 伪元素 ::
      	7. 子选择器(>/\n)、相邻选择器(+/,)

计算权重：!important最高，不推荐

1. 第一等：style='' 内联样式  **1000**
2. 第二等：ID选择 #id  **100**
3. 第三等：class/伪类/属性选择器 **10**
4. 第四等：元素 **1**
5. *、>、+ **0**

![权重实例](http://www.nowamagic.net/csszone/images/priority_rules_2.jpg)



#### 三栏布局

1. float : 左右浮动
2. flex：左右给固定width,中间flex:1自由撑开
3. position：全部使用绝对定位

#### BFC [地址](https://blog.csdn.net/weixin_43801564/article/details/89352435)

[视频](https://www.bilibili.com/video/BV1h54y1D7rb?from=search&seid=17512387739467067458)

​	简介：**BFC内部的元素不会对外部产生影响**。浮：作用：**清除浮动和解决盒子塌陷**

1. position: absolute/fixed
2. float: 不为none
3. overflow: 不是visible(不设置浮动元素会溢出)
4. display: inline-block(解决外边距塌陷)/flex

