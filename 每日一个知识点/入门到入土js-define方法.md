## define

**CommonJS**-提出了许多新的JavaScript架构方案和标准，希望能为前端开发提供银弹，提供统一的指引。

**AMD规范就是其中比较著名一个**--**即异步模块加载机制**

# AMD是什么

**AMD规范简单到只有一个API，即define函数**

- **define([module-name?], [array-of-dependencies?], [module-factory-or-object]);**
  - **其中：**
    - **module-name: 模块标识，可以省略。**
    - **array-of-dependencies: 所依赖的模块，可以省略。**
    - **module-factory-or-object: 模块的实现，或者一个JavaScript对象。**

