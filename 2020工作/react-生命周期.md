### (taro)componentWillMount()组件将要加载

简介：

### (taro)render

### (taro)componentDidMount()组件加载完成：请求axios数据，组件传值接受

### componentWillReceiveProps()将要接受父props

简介：父组件的props值发生变化时

### shouldComponentUpdate(nextProps, nextState)子组件应该更新

​	简介 ： 如果状态一直很更新，render会一直更新，所以在shouldComponentUpdate写阻止更新

```javascript
if(this.state.name===nextState.name)return false
```

### (taro)componentWillUpdate()组件将要更新

### (taro)componentDidUpdate()组件更新完成

### (taro)componentWillUnmount()组件将要销毁