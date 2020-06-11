### export 导出的是对象，需要解构

```
export {getData, setDate}
```

### export default 导出的是对象

```
export default {getData, setDate} 引入时候不能解构，使用的时候用‘utils.getData’
```

### export {default as getData}