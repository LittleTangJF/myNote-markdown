## 开始

​	 起步

1. ```js
   // create-react-app
   mkdir my-project
   cd ./my-project
   sudo npm install -g create-react-app
   ```

   安装react + t s 初始化

   ```js
   npx create-react-app react-initial --template typescript
   yarn create react-app my-app
```
   
#### webpack 配置修改
   
   - “我可不可以修改一下 less 的一些全局配置？”
   - “我可不可以修改入口文件呢？”
- “相对路径取别名怎么做？
   
2. ```js
   yarn add react-app-rewired customize-cra -D
   
   //修改package.json
   "scripts": {
     "start": "react-app-rewired start",
     "build": "react-app-rewired build",
     "test": "react-app-rewired test",
     "eject": "react-scripts eject"
   },
   ```

    安装完毕，紧接着在项目下创建一个 config-overrides.js 来修改你的一些配置，相关配置可参考 [API 文档](https://github.com/arackaf/customize-cra/blob/master/api.md)，以下是我自己本身的一些配置仅供大家参考

   ```js
   const path = require("path");
   const {
     override,
     addDecoratorsLegacy,
     disableEsLint,
     addLessLoader,
     useBabelRc,
     addWebpackAlias,
   } = require("customize-cra");
   
   module.exports = {
     webpack: override(
       useBabelRc(),
       addDecoratorsLegacy(),
       disableEsLint(),
       addLessLoader({
         javascriptEnabled: true,
         modifyVars: {
           "@primary-menu-color": "#7638ff",
           "@primary-menu-background-color": "rgba(118, 56, 255, 0.05)",
           "@darker-color": "rgba(0,0,0,0.85)",
           "@dark-color": "rgba(0,0,0,0.65)",
           "@light-color": "rgba(0,0,0,0.45)",
           "@layout-header-background": "#FFFFFF",
           "@font-family": "PingFang SC",
           "@card-shadow": "0px 10px 20px 0px rgba(151,151,151,0.12)",
           "@border": "solid 1px rgba(0,0,0,0.1)",
           "@border-radius-base": "4px",
         },
       }),
       addWebpackAlias({
         ["@"]: path.resolve(__dirname, "src"),
       })
     ),
   };
   ```

   由于我的配置中使用了 less-loader 插件，所以我们安装一下 less-loader 插件，顺便安装一下 @types/react (React 模块的声明文件)

   ```js
   npm install less --save-dev
   npm install less-loader@5.0.0 --save-dev
   npm install @types/react --save-dev
   // yarn
   yarn add less less-loader@5.0.0 @types/react -D
   
   ```

   格式化代码 .prettierrc

   ```js
   yarn   add    prettier husky lint-staged    -D
   // 然后修改你的 package.json
   "eslintConfig": {
     "extends": [
       "react-app"
     ]
   },
   "lint-staged": {
     "src/**/*.{ts,tsx,less}": [
       "prettier --write"
     ]
   },
   "husky": {
     "hooks": {
       "pre-commit": "lint-staged"
     }
   },
     
     // .prettierrc
     {
     "proseWrap": "never",
     "singleQuote": true,
     "trailingComma": "all",
     "semi": false
   }
   ```

   非格式化.prettierignore

   ```
   **/*.svg
   package.json
   .umi
   .umi-production
   /dist
   .dockerignore
   .DS_Store
   .eslintignore
   *.png
   *.toml
   docker
   .editorconfig
   Dockerfile*
   .gitignore
   .prettierignore
   LICENSE
   .eslintcache
   *.lock
   yarn-error.log
   .history
   ```

   其他优秀的npm包

   ```js
   npm install react-dom @types/react-dom react-router-dom @types/react-router-dom --save
   npm install lodash --save
   npm install antd --save
   npm install echarts --save
   npm install axios --save
   ```

   

