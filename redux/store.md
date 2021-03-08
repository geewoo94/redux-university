---
description: 상태 관리를 위한 단 하나의 store입니다.
---

# Store

createStore를 통해 반환된 객체입니다.

store가 갖고있는 여러가지 메소드를 통해 store의 상태를 변경하고 변경된 상태를 감지하는 법을 알아봅시다.

## Store 메소드   

* getState
* dispatch
* subscribe
* replaceReducer

### getState

리듀서가 **현재** 갖고있는 상태를 즉 반환합니다. 

```javascript
const currentState = store.getState()
```

### dispatch

리듀서의 상태를 변환 할 수 있는 유일한 메소드 입니다.

```javascript
const action = () => ({ type: a, payload: 1 })
store.dispatch(action())
```

액션은 [리듀서](../dictionary/example-code.md#reducer)로 보내지게 됩니다. 

### subscribe

reducer의 상태 변경이 감지 됐다면 이 안의 콜백 함수가 실행되게 됩니다.

주로 직접 사용하지는 않고 react의 render함수와 같은 것들이 들어가게 됩니다.

```javascript
const unsubscribe = store.subscribe(listener)
unsubscribe() // 반환된 값으로 리스너를 해지합니다.
```

### replaceReducer

현재 사용되고 있는 리듀서를 통째로 뒤엎습니다.

잘 사용되지는 않고 reducer를 동적으로 받아왔을때 사용 될 수 있을겁니다.

```javascript
store.replaceReducer(nextReducer)
```

