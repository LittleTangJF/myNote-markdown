## 前言

​		历史上，js一直没有模块(module)体系，无法将一个项目拆分成多个模块文件;

​		不过在v13.2版本，nodejs已经实现了ES6模块语法，还未正式替换，在考察阶段。v13.2版本将js文件以 .mjs结尾，nodejs将它视为ES6模块。以 .cjs结尾则视为CommonJS模块。

#### CommonJS 

> 一种模块规范，最初被应用于 Nodejs，成为 Nodejs 的模块规范=>**服务端的js**

#### ES6 Module

> ES6 起，引入了一套新的 ES6 Module 规范；但目前浏览器对 ES6 Module 兼容还不太好，我们平时在 Webpack 中使用的 export导出 和 import导入，会经过 Babel 转换为 CommonJS 规范。

#### CommonJS 和ES6 Module区别

- **加载**

  - CommonJS 加载整个模块，ES6  Module可以单独加载某个方法。

- **加载的时机**

  - CommonJS 模块是运行时加载，ES6  Module是编译时输出接口。

  - ```js
    const bModule = require('./' + fileName)//支持表达式
    ```

    

- **输出方式**

  - CommonJs ：导入require,导出module.exports={}/exports.变量
  - ES6 Module：导入import,导出export

- 值的变化

  - CommonJs 值的深拷贝，ES6 Module 是值的引用，原来的模块变化，加载的值也跟着变化

- CommonJs 的 this 是当前模块，ES6 Module的 this 是 undefined

## 总结

​		开发中写的 `ES6` 模块最终都会被打包工具处理成 `CommonJS` 模块，以便兼容更多环境，同时也能和当前社区普通的 `CommonJS` 模块融合。

