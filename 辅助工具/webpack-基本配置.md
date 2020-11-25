# webpack

## webpack赋能

- 模块打包器（Module bundler）
- 模块加载器（Loader）=> 针对环境兼容问题，引入Loader进行转换
- 代码拆分（Code Spliting）=> 赋予 [拆包 ]()功能
- 资源模块（Asset Module）=>  css-loader 配置了多个loader，执行时是从后往前执行。

> **Loader是Webpack实现前端整个模块化的核心，借助于Loader就可以加载任何类型的资源**

## 快速上手Loader

#### 1..webpack.config.js

- ```js
  const path = require('path')
  
  module.exports = {
    entry: './src/main.js',
    output: {
      filename: 'bundle.js',
      path: path.join(__dirname, 'output') // 必须是绝对路径
    }
  }
  /*
  * 配置完成后，Webpack会以./src/main.js为打包入口，把打包结果放在output/bundle.js中。
  */
  ```

> 设置 打包 环境  命令   Webpack命令传入`--mode`参数      分别是production    development     none；
>
> build : Webpack会默认使用production模式工作    [私有作用域](https://www.manongdao.com/article-2391380.html)

#### 2.配置Module

- ```js
  module: {
    rules: [
      {
        test: /.css$/, // 正则
        use: [
          'style-loader',// +1  将css loader转换过后的结果通过style标签的形式追加到页面上
          'css-loader'  // 运行后发现无效，因为他只是加载css成为js模块
        ]
      }
    ]
  }
  // todo rules的规则是从下往上依次执行  yarn add css-loader  style-loader
  ```

- <img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4e6737e0ee094a6aa671852e76054280~tplv-k3u1fbpfcp-watermark.image" alt="img" style="zoom:33%;" />

#### 3.文件资源加载器 [不常用]()

- ```js
  rules: [
    {
      test: /.png$/,  // 不会显示，需要设置在output中添加publicPath属性 dist/  网站的跟目录
      use: 'file-loader' 
    }
  ]
  // 项目当中的图片、字体，这些文件是没办法通过JS的方式去表示的  yarn add file-loader
  ```

#### 4.URL加载器  

- ```js
  {
    test: /.png$/,
    use: 'url-loader',
    options: {
        limit: 10 * 1024 // 10 KB 以下的转换
      }
  }
    // data: lshfoiawgvna 编码的base64 url
  ```

#### 5.ES6 转换加载器

- ```js
  {
    test: /.js$/,
    use: {
      loader: 'babel-loader',
      options: {
        presets: ['@babel/preset-env']  //@babel/preset-env就已经包含了全部的ES最新特性。
      }
    }
  }
  ```

#### 6.html-loader [不常用]()

- ```js
  {
    test: /.html$/,
    use: {
      loader: 'html-loader',
      options: {
        attrs: ['img:src', 'a:href']  //的HTML代码中图片标签的src属性以及a标签的href属性
      }
    }
  }
  ```

## 快速上手Plugin

#### 1.clean-webpack-plugin

- ```js
  const { CleanWebpackPlugin } = require('clean-webpack-plugin')
  ...
  // 自动清除输出目录插件
  plugins: [
    new CleanWebpackPlugin()
  ]
  ```

#### 2.html-webpack-pligin

- ```js
  const { CleanWebpackPlugin } = require('clean-webpack-plugin')
  const HtmlWebpackPlugin = require('html-webpack-plugin')
  ...
  // 自动生成HTML插件
  plugins: [
    new CleanWebpackPlugin(),
    new HtmlWebpackPlugin()
  ]
  ```

## 快速上手Webpack Dev Server

- ```js
  devServer: {
    proxy: {
      '/api': {
        // http://localhost:8080/api/users -> https://api.github.com/api/users
        target: 'https://api.github.com',
        // http://localhost:8080/api/users -> https://api.github.com/users
        pathRewrite: {
          '^/api': ''
        },
        // 不能使用 localhost:8080 作为请求 GitHub 的主机名
        changeOrigin: true
      }
    }
  },
  ```

> 在creat-react-app 使用插件[http-proxy-middleware]() 设置跨域

## 快速上手Source Map

- ```js
  devtool： 'cheap-module-source-map'  //development
  devtool： false //production
  ```

## 原理

​		[Webpack]()会根据我们的配置找到其中的一个文件作为打包的入口，一般情况下这个文件都是JavaScript文件，然后会顺着我们入口文件当中的代码，根据代码中出现的import或者是像reuqire之类的语句解析推断出来这个文件所依赖的资源模块，然后分别去解析每个资源模块对应的依赖，最后就形成了整个项目当中文件依赖关系的关系树，

​	![img](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d39935b1ff7c467fa43f5adea4c7d01f~tplv-k3u1fbpfcp-watermark.image)

​		[Loader]()实际上是一种管道的概念，可以将此次loader的结果交给下一个loader去处理，对于通过一个资源可以依次使用多个loader，通过多个loader去完成一个功能，例如css-loader -> style-loader的配合。

