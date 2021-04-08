## Promise

### 直接开始

技巧

1. 函数自执行
2. 内部函数传參 例如.then(function(res){}, function(res){})res是promise保存到内部的value然后传给then返回
3. 外部函数传參 例如executor(内部的resolve函数, 内部的rejected函数) 接收到外部promise的参数传进来，内部函数执行

- ```js
  //三个状态
  const PENDING = 'pending'
  const FULFILLED = 'fulfilled'
  const REJECTED = 'rejected'
  
  function Promise(executor) {
    var _this = this
    this.state = PENDING // 状态
    this.value = undefined // success
    this.reason = undefined // fail
  
    this.onFulfilled = [] // 存success函数去执行，可能有多个then不能用变量
    this.onRejected = [] // 存fail函数去执行，可能有多个then不能用变量
    function resolve(value) {
      if(_this.state === PENDING){
        _this.state = FULFILLED
        _this.value = value
        _this.onFulfilled.forEach(fn => fn(value))
      }
  
    }
    function reject(reason) {
      if(_this.state === PENDING){
        _this.state = REJECTED
        _this.reason = reason
        _this.onFulfilled.forEach(fn => fn(reason))
      }
    }
    // 执行
    try{
      executor(resolve, reject)
    }catch (e){
      reject(e)
    }
  }
  
  Promise.prototype.then = function(onFulfilled, onRejected){
    if(this.state === FULFILLED){ // 成功
      typeof onFulfilled === 'function' && onFulfilled(this.value)
    }
    if(this.state === REJECTED) { // fail
      typeof onRejected === 'function' && onRejected(this.reason)
    }
    // 当then里面函数运行时，resolve由于是异步执行的，还没有来得及修改state，此时还是PENDING状态；因此我们需要对异步的情况做一下处理。
    if(this.state=== PENDING){ // 把成功需要的
      typeof onFulfilled === 'function' && this.onFulfilled.push(onFulfilled)
      typeof onRejected === 'function' && this.onRejected.push(onRejected)
    }
  }
  var myP = new Promise(function(resolve, reject){
    console.log('执行')
    setTimeout(function(){
      reject(3)
    }, 1000)
  });
  
  myP.then(function(res){
    console.log(res)
  },function(err){
    console.log(err)
  });
  
  
  
  ```

  