## 开始上手

#### 一、路由配置

- ```react
  yarn add react-router-dom
  // route.js
  const BasicRoute = () => (
      <HashRouter>
          <Switch>
              <Route path="/"  exact component={Login} />
              <Route path="/draw" exact  component={Draw} />
          </Switch>
      </HashRouter>
  );
  //index.js
  
  import Router from './route'
  
  ReactDOM.render(
      <Router/>,
      document.getElementById('root')
  );
  ```


#### 二、配置axios

- ```react
  // 普通配置
          axios({
              url: 'https://t600test.bellonline.cn/marketing/index.php/api/lottery/get_group_success_mobile',
              method: 'post',
              headers:{Content-Type:'application/json'}，
              data:{}
          }).then(({data}) => {
              console.log(data, '获取开团')
          }).catch(err => {
              this.isCatchErr(err)
          })
  ```


#### 三、配置跨域

​		通过middleware中间件的方式设置proxy

- ```js
  yarn add http-proxy-middleware
  
  // 在src目录中新建setupProxy.js文件
  const { createProxyMiddleware } = require('http-proxy-middleware')
  module.exports = function (app) {
    app.use(createProxyMiddleware ('/api/admin', {target: 'http://116.62.45.68:8002/',  changeOrigin: true, pathRewrite: {'/api/admin': '/admin'}})) // 开发环境
    app.use(createProxyMiddleware ('/api/yami/index.php/api', {target: 'https://t400apitest.bellonline.cn/',  changeOrigin: true, secure: true, pathRewrite: {'/api/yami/index.php/api': '/yami/index.php/api'}})) // 市场的开发环境
    // app.use(createProxyMiddleware('/api/admin', { target: 'https://t400apitest.bellonline.cn/', changeOrigin: true, secure: false })) // 测试环境
  
  }
  
  ```

#### 四、配置多环境

- ```js
  // 开始配置 多环境 要使用到 react-app-rewired dotenv-cli 
  yarn add react-app-rewired dotenv-cli
  
  // 一个用于按需加载组件代码和样式的 babel 插件
  npm install babel-plugin-import -D
  
  // react-scripts 升级到 2.1.2 以后破坏了 react-app-rewired，react-app-rewired的新版本删除所有方法injectBabelPlugin，这些方法被移动到一个名为’customize-cra’的新包中了
  yarn add customize-cra --dev
  
  // 如果less
  yarn add less
  yarn add --dev less-loader
  
  // 根目录下config-overrides.js
  const {
      override,
      fixBabelImports,
      // addLessLoader,
  } = require("customize-cra");
  
  
  module.exports = override(
      fixBabelImports("import", {
          libraryName: "antd", libraryDirectory: "es", style: 'css' // change importing css to less
      }),
      // addLessLoader({
      //   javascriptEnabled: true,
      //   modifyVars: { "@primary-color": "#1DA57A" }
      // })
  
  );
  // 多环境：根目录创建 .env.development 和 .env.production 两个文件`
  // .env.development
  REACT_APP_ENV=development
  // .env.production
  REACT_APP_ENV=production
  
  // 解决win mac下的打包环境问题
  yarn add cross-env
  ```

  