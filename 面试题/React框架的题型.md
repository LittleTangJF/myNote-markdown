## React 的 diff 算法工作过程

**传统Diff**

​	diff算法即差异查找算法

**React Diff**

​	React Diff算法的差异查找实质是对两个JavaScript对象的差异查找

​	**策略**

​			1、只同级比较

​			2、不同类的组件会直接替换

​			3、唯一标识key

​	**过程**----React更新阶段

​			1、文本：text节点的更新很简单，直接更新文案

​			2、Dom: 节点不同，React直接删除前面的节点，然后创建并插入新的节点。

​			3、组件: 不同类的组件会直接替换



## React 的事件机制

​	***react**的事件是**合成事件**((Synethic event)*，React并没有使用原生的浏览器事件，事件处理程序接收到的是SyntheticEvent的实例

​	**和原生事件的区别**

​				1、合成事件全部委托到document上，而原生事件绑定到DOM元素本身

​				2、写法不同，合适事件是驼峰写法

​	**为什么手动绑定this**

​				通过事件触发过程的分析，回调函数是直接调用调用的，并没有指定调用的组件，不绑定this`是`undefined



## React 中的 setState 是同步还是异步

**异步**

​		1、合成事件

​		2、钩子函数

**同步**

​		1、原生事件：addeventListener、dom中的原生事件

​		2、setTimeout 

## React、Vue 的区别

**同**

​		1、**基于Virtual DOM模型**

​		2、其他功能如路由和全局状态管理交给相关库

​		3、**响应式**和**组件化**的视图组件

**异**
				1、react灵活的结构和可扩展性

​		 2、 vue 是一个 framework，它更加注重的是框架，react 是一个 library，不负责工具链的事情

​		 3、Vue 是响应式的，React 是手动setState

## React 中组件复用

**render props模式**

**高阶组件（HOC）**

​		定义：如果一个组件 接受一个或多个组件作为参数并且返回一个组件 就可称之为 高阶组件

1. ```js
   import React from 'react';
   
   function withCounter(Component) {
     return class extends React.Component {
       state = { number: 0 };
       componentDidMount() {
         setInterval(() => {
           this.setState({ number: this.state.number + 1 });
         }, 1000);
       }
       render() {
         return (
           <Component number={this.state.number} />
         )
       }
     }
   }
   ```

   

**自定义hooks**

1. 

   ```js
   import React, { useState, useEffect } from 'react';
   
   /**
    * 自定义hooks,以use开头的名字并且使用内置的hooks
    */
   function useNumber() {
     let [number, setNumber] = useState(0);
   
     useEffect(() => {
       setInterval(() => {
         setNumber(number => number + 1);
       }, 1000);
     }, []);
   
     return [number, setNumber];
   }
   ```

   

## React 的 Fiber 架构

**16.8版本之前**

​	挂载阶段：

- `constructor()`
- `componentWillMount()`
- `render()`
- `componentDidMount()`

更新阶段：

- `componentWillReceiveProps()`
- `shouldComponentUpdate()`
- `componentWillUpdate()`
- `render()`
- `componentDidUpdate`

卸载阶段：

- `componentWillUnmount()`



**任务分片**也就是 16 ms 必须渲染一次保证不卡顿的情况下，React 会每 16 ms（以内） 暂停一下更新，返回来继续渲染动画。----------潜水员会每隔一段时间就上岸，看是否有更重要的事情要做。**phase1的生命周期函数**

**目的**：react16增加fiber结构，其实并不是为了减少组件的渲染时间，事实上也并不会减少，最重要的是现在可以使得一些更高优先级的任务，如用户的操作能够优先执行，提高用户的体验，至少用户不会感觉到卡顿~

## 老版本的 React 的某些生命周期被废弃的理由

1、componentWillMount（）

​		理由：函数的功能完全可以使用componentDidMount和constructor来代替，fiber或者导致componentWillMount多次更新，服务端更新会多次请求

​		方案：componentDidMount

2、componentWillReceiveProps（）
				理由：导致多次更新，一次更新中被调用多次

-  

  ```js
  // 旧
  componentWillReceiveProps(nextProps){
   if(nextProps.tab!=this.props.tab){
    this.setState({
      tab:nextProps.tab
    });
    this.tabChange();
   }
  }
  //新
  static getDerivedStateFromPorps (nextProps,prevState){
   //2
   if(nextProps.tab!=prevState.tab){
     return {
      tab:nextProps.tab
     };
   }
   return null;
  }
  
  componentDidUpdate(prevProps,prevState){
    this.tabChange();
  }
  ```

  3、componentWillUpdate（）

  ​	理由：	导致多次更新，一次更新中被调用多次	

  ​	方案：用componentDidUpdate	

## React 性能优化

​	1、*将this指向放在constructor中执行，在复杂的组件开发中节约性能*，别在j s x中执行

​	2、shouldComponentUpdate生命周期函数==>避免重复渲染 ==需要更新return true

​	3、React.memo()：是一个高阶组件

​	4、react的高阶组件[react-loadable](https://github.com/jamiebuilds/react-loadable)进行动态import

- 

  ```js
  import Loadable from 'react-loadable';
  import Loading from './loading-component';
  
  const LoadableComponent = Loadable({
    loader: () => import('./my-component'),
    loading: Loading,
  });
  
  export default class App extends React.Component {
    render() {
      return <LoadableComponent/>;
    }
  }
  ```

  