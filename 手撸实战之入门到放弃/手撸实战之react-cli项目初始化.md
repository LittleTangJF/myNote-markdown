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

