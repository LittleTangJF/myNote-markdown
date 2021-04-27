## 开始



1.  npm账号
     	oldtom   TJFshuai351146  验证邮箱

2. npm init

3. 创建index.js

   1. ```js
      ;(function (global, factory) {
        typeof exports === 'object' && typeof module !== 'undefined' ? module.exports = factory() :
          typeof define === 'function' && define.amd ? define(factory) :
            global.moduleName = factory()
      }(this, (function () {
        var test = {
          sayHi: function () {
            console.log('hi');
          }
        };
       
        return test
      })))
      ```

      

4. 登陆 npm adduser

5. `发布npm publish`

6. 改版本再发布

   ### 遇到问题总结

   - 用了淘宝镜像源 - 换成npm的源。
   - 包名重复 - 删掉之前的包，改个名字。
   - npm账户没有验证邮箱 - 验证邮箱。
   - vpn冲突 - 关掉所有vpn再次尝试。