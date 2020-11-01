#### 1.联合类型  |

```typescript
let name : string | null |undefind =''
***
type NullAndStr = string | null;
let name :NullAndStr=''
```

#### 2.可选Partial

```typescript
type PartialUser = Partial<userProps & buttonProps> //转变User/buttonProps接口成可选
function todo(tdo: PartialUser)
```

### 3.继承User接口

```typescript
type  MyPick<T,keys extends keyof T> = { [p in keys ]: T[p]}
type UserAgeGender = MyPick<User, 'age' | 'gender'>
```



#### 4.交叉类型 &

