### 基本步骤

1. **entry**(js)
2. **output(**自定义输出文件夹)
3. **loader**()
	module{less/css/img, options{配置操作限制的规则如大小limit}}
4. **plugin**[  **new plugins()**]
	**htmlWebpackPlugin**(minify清理空格注释),  mini-css-extract抽离**Css**,  optimize-css-assets-webpack压缩**Css**, 
5. **mode**(环境设置) 
	改为**production**会自动压缩js
6. **devServer**()        
	配置本地服务：属性compress压缩,contentbase路径，post端口   **启动**：npx webpacck-dev-server