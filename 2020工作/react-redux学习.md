### store.js

```javascript
import { createStore,  compose} from 'redux'
import reducer from './reducer'
const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;
const store = createStore(reducer, /* preloadedState, */ composeEnhancers())
export default store
```

### reducer.js

```javascript
const defaultState = {
  data: ["今天星期一", "学习rudux", "下午23点钟"],
  inputValue: "write something",
};
export default (state = defaultState, action) => {
    console.log(action);
    // reducer里只能接受state,不能改变state
    if(action.type==='changeInput'){
        let newState = JSON.parse(JSON.stringify(state))
        newState.inputValue = action.value
        return newState
    }
  return state;
};

```

### react-thunk中间件[安装](npm install --save redux-thunk)

​	简介	使用 `thunk` 等中间件可以帮助在 Redux 应用中实现异步性