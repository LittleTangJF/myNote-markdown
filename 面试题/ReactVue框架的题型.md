

## Router

http://shanhuxueyuan.com/news/detail/137.html

hash路由  onhashchange

history  window.history

## Vue框架

### 初次渲染

- compile解析模板-->render函数
- 触发响应式，监听data属性的getter属性收集，就是往dep订阅器里添加watcher的过程
- 执行render函数，生成v node，patch

### 更新

- 修改data属性触发setter调用dep里的notify(),通知他内部所有的watcher进行视图更新
- 重新执行render函数，生成newVnode -->patch

## React 的 diff 算法工作过程

**传统Diff**

​	diff算法即差异查找算法

**React Diff**

​	React Diff算法的差异查找实质是对两个JavaScript对象的差异查找

​	**策略**

​			1、**同层节点**之间相互比较，不会垮节点比较

​			2、发现不同直接跳出比较

​			2、不同类的组件会直接替换

​			3、唯一标识key

​	**过程**----React更新阶段 **render函数生成虚拟Dom** diff算法计算出差异更新

​			1、文本：text节点的更新很简单，直接更新文案

​			2、Dom: 节点不同，React直接删除前面的节点，然后创建并插入新的节点。

​			3、组件: 不同类的组件会直接替换

## React为什么组件是大写

1. 区分于html标签写法
2. React.createElement(type， config， children) babe转义 type是一个变量--组件， 否则当成字符串

## React 的事件机制

​	***react**的事件是**合成事件**((Synethic event)*，React并没有使用原生的浏览器事件，事件处理程序接收到的是SyntheticEvent的实例

​	**和原生事件的区别**

​				1、合成事件**全部委托到document**上，而原生事件绑定到**DOM元素**本身

​				2、写法不同，合成事件是**驼峰写法**

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

## React优化

[地址](https://segmentfault.com/a/1190000016259872)

1、code split 拆包

2、shouldComponentUpdate -----Hooks`组件则可以使用`React.memo

3、动态import

4、组件拆分解耦

5、bind函数优化

6、不要滥用props引起的重绘

7、列表类组件优化

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

## Redux

[地址](https://github.com/xuwening/blog/blob/193057c0c08b79e1fb03d500d1c28b4564e5d8f3/mdFile/redux%E5%8E%9F%E7%90%86%E8%A7%A3%E6%9E%90.md)

redux 有三个核心概念：

1. Action **更新** Store 的具体单元。

2. Reducer 是**改变** Store 的唯一方式，指明如何更新 Store。

3. Store 是所有的状态数据，对用户来说是**只读**的，不可改变。

   ​     redux 只做状态管理，不做View的处理，因此 redux 需要配合其他框架一起使用，本章使用的 View 框架是 React。

了解了 redux 的实现机制，你会发现 redux存在一些问题。

1. redux 存在性能问题。js 是单线程的，每次 dispatch 都是遍历执行立即更新 state，会造成卡顿。
2. redux 重复性代码依然多，每个页面都需要处理 subscribe 和 dispatch。
3. redux 增加了代码复杂性，但针对复杂项目，这种代价是值得的。

`applyMiddleware`和`bindActionCreators`。

返回 actions 的函数中就用到了`bindActionCreators`，用来自动执行 dispatch(action)功能。

在 Provider 和 CounterApp 之间动态插入了 **Connect 组件**。至此，我们只要建立 redux 和 react 的关联，将 Action 与 view 事件绑定，其他都可以自动化了。