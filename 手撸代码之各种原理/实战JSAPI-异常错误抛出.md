## Error

#### API

#### 1.如何捕获错误

> 最常见的ReferrenceError异常错误

- try ....   catch ....
- Promise
- await

#### 2.如何优雅的抛出异常

- 自定义**CustomError** 

  ```js
  /**
   * @file 错误类型汇总
   * @author arlenyang
   */
  class ApiError extends Error {
      /**
       * @constructor
       * @param {string} code 错误码
       * @param {string} msg 中文描述  原来是Error.message
       */
      constructor(code, msg) {
          super(msg);
  
          if (Error.captureStackTrace) {
              // 
              Error.captureStackTrace(this, ApiError ); //this.constructor
          }
          this.code = code;
          this.msg = msg;
      }
  	// 源码释义：判断某个对象值属于哪种内置类型
      toString() {
          return `Api${this.stack}\n    ${this.msg}, errCode: ${this.code}`;
      }
  }
  let a = new ApiError(1,'aaa'); console.log(a.toString())
  //   ApiError: aaa
  //   at <anonymous>:22:10
  //   aaa, errCode: 1
  // 错误类型
  ApiError.MYSQL_QUERY_ERROR = 1;
  ApiError.MYSQL_QUERY_ERROR_DESC = '查询数据失败';
  ```

  【Object.prototype.toString.call()】

  > 被调用时会执行以下步骤

  - 获取this对象的[[Class]]属性的值.

    - ,原生对象的[[class]]内部属性的值一共有10种.分别是:"Array", "Boolean", "Date", "Error", "Function", "Math", "Number", "Object", "RegExp", "String".

  - 计算出三个字符串"[object ", 第一步的操作结果[class], 以及 "]"

    ```js
    Object.prototype.toString.call(Error()) =>>>>>>"[object Error]"
    ```

    

  【Object.getOwnPropertyNames()】