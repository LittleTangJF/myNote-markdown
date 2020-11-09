#### 1.for await of

- 遍历遍历异步迭代器

#### 2.Promise.prototype.finally()

- Promise.prototype.finally() 方法返回一个Promise，在promise执行结束时，无论结果是fulfilled或者是rejected，在执行then()和catch()后，都会执行finally指定的回调函数。

> **避免同样的语句需要在then()和catch()中各写一次的情况**。

#### 3.新的正则表达式特性

- ###### 命名捕获组

```js
const re = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/;
const match = re.exec('2019-01-01');
console.log(match.groups);          // → {year: "2019", month: "01", day: "01"}
console.log(match.groups.year);     // → 2019
console.log(match.groups.month);    // → 01
console.log(match.groups.day);      // → 01
```

```js
const re = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/
const usDate = '2018-04-30'.replace(re, '$<month>-$<day>-$<year>')
console.log(usDate) // 04-30-2018
```

- #### Lookbehind 后行断言 (?=) 先行断言(?<=)