## redux

- **三大原则**

1. 单一数据源---全局state管理
2. state**只读**
3. reducer是纯函数---结果只依赖于输入的**参数**、没有**副作用**

- ### 缺点
  - 一个组件所需要的数据，必须由父组件传过来，而不能像 flux 中直接从 store 取。
  - 当一个组件相关数据更新时，即使父组件不需要用到这个组件，父组件还是会重新 render，可能会有效率影响，或者需要写复杂的 shouldComponentUpdate 进行判断。

- ### Redux的中间件

  自定义拦截action -> reducer 的过程。变为 action -> middlewares -> reducer。这种机制可以让我们改变数据流，实现如异步 action ，action 过滤，日志输出，异常报告等功能。



- ### 流程
  - action只是描述要发生的事件
  - reducer根据action的描述，改变state
  - store用来保存state
    - getState() 
    - dispatch(action) 
    -  subscribe(listener)注册监听器---返回的函数注销监听器

- 

- ### 部分源码

  **bindActionCreators.js**

  ​	bindActionCreator将值为actionCreator的对象转化成具有相同键值的**对象**，每一个actionCreator都会被dispatch所包裹调用

  **createStore.js**

  ​	CreateStore(reducer)作为生成唯一store的函数

- ```js
  return {
    dispatch,
    subscribe,
    getState,
    replaceReducer,
    [$$observable]: observable
  }
  ```

  是谁调用了**subscribe**呢？**dispatch**又是谁调用的呢？不出意外就是**react-redux**了

  ### 与react框架的结合--react-redux

  ​		react-redux在Provider里进行subscribe，connect的参数mapDispatchToProps里的dispatch就是redux的dispatch，用react的context API来实现更新机制

  - **Provider**
  - mapStateToProps(state,ownProps)--当前Redux store state映射到展示组件的props中
  - mapDispatchToProps(dispatch,ownProps)--接受dispatch方法并返回期望注入到展示组件的props中的回调方法

  provider

  - ```js
    subscribe() {
        const { store } = this.props
    
        this.unsubscribe = store.subscribe(() => { // 调用redux的createStore里的subscribe函数了
          const newStoreState = store.getState()
    
          if (!this._isMounted) {
            return
          }
    
          this.setState(providerState => {
            // If the value is the same, skip the unnecessary state update.
            if (providerState.storeState === newStoreState) {
              return null
            }
    
            return { storeState: newStoreState }
          })
        })
    
        // Actions might have been dispatched between render and mount - handle those 看一眼这个注释
        const postMountStoreState = store.getState()
        if (postMountStoreState !== this.state.storeState) {
          this.setState({ storeState: postMountStoreState })
        }
      }
    
    ```

    