### Es7

#### 1.Array.prototype.includes

#### 2.求幂运算符

### Es8

#### 1.String拓展

- String.prototype.padStart
- String.prototype.padEnd

#### 2.Object对象拓展

- Object.values
- Object.entries

#### 3.async函数

- 并行处理异步

```js
async function asyncFunc() {
    const [result1, result2] = await Promise.all([
        otherAsyncFunc1(),
        otherAsyncFunc2()
    ]);
    console.log(result1, result2);
}
//以上遇到报错会停止，所以用=》 Promise.allSettled
```

- 顺序处理异步

```js
async function asyncFunc() {
    const result1 = await otherAsyncFunc1();
    console.log(result1);
    const result2 = await otherAsyncFunc2();
    console.log(result2);
}
```

