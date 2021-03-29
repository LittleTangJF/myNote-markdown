## 虚拟Dom

把Dom结构存放在js对象中，并通过虚拟DOM类库与‘真实的’DO M 同步协调。

用js对象表示虚拟DOM信息和结构，当状态发生变化时，重新渲染这个js对象结构，这个对象就是虚拟DOM。

## JSX

react16: babel-loader会编译jsx为react.createElement(...)

react17: 是自动从package引入新的入口函数并调用，

ReactDom.render 负责组件的更新和初次渲染

## vnode

1. type  原生标签 文本节点 函数
   1. 原生： document.CreateElement
   2. 文本： document.CreateTextNode
   3. 函数： 执行
   4. 类组件： 实例化，再执行reader
   5. fragment： 直接遍历子节点 create Document Fragment
2. props  children

## 函数组件 类组件 isReactComponent 判断 

## fragment 可以用key

## reconciliation协调

在某props或者state更新时，相同的render方法会返回一颗不同的树，react在这两棵树之间会判断差异，并进行最效率化的更新当前UI



