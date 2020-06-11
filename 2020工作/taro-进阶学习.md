### 条件渲染

###  1.&&

```react
render> const isLoggedIn = this.props.isLoggedIn
{isLoggedIn && <Text>已登录</Text>}
{!isLoggedIn && <Text>未登录</Text>}
```

 2. 三元运算符

    ```
     {isLoggedIn
            ? <Text>已登录</Text>
            : <Text>未登录</Text>
          }
    ```

### 传参bind（this,参数）

​	简介：接受accept(param, e) :param 是参数，e是对象，通常用e.stopprposz阻止事件冒泡

### 组件与children

​	简介： 为了封装公共组件，类似于vue里的slot插槽，封装组件如dialog.js内**{this.props.childen}** childen就是不同的组件显示内容