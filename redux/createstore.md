# createStore

## `createStore(reducer, [preloadedState], [enhancer])`

리덕스의 store를 생산합니다. redux에서는 **하나의 store만** 사용하기를 **강력히 권장합니다.** 

### [reducer](../dictionary/example-code.md#reducer)

reducing 함수이다. action handler를 통해 다음 상태트리를 반환합니다.

createStore를 실행시키면 최초에 한번 reducer가 작동됩니다.

작동된 reducer에 따라 최초 상태 값이 결정됩니다. **아래 코드를 통해 더욱 자세하게 알 수 있습니다.** 

### preloadedState

최초의 상태를 정의 할 수 있습니다. 만약 [combineReducers](combinereducers.md)로 reducer를 만들었다면 그에 대응하는 최초의 상태를 정의해줘야 합니다. 

### enhancer

추가적인 third party를 사용할수 있습니다. redux에서 기본적으로 제공되는 인핸서는 [applyMiddleware](applymiddleware.md)가 있습니다. 여러가지 enhancer를 사용하고 싶다 compose를 사용하여 결합할수 있습니다. 

```typescript
if (typeof enhancer !== 'undefined') {
  if (typeof enhancer !== 'function') {
    throw new Error('Expected the enhancer to be a function.')
  }

  return enhancer(createStore)(
    reducer,
    preloadedState
  )
}
```

위 코드는 redux 소스코드 입니다. enhancer는 createStore를 받는 HOF입니다. 

#### 예

```typescript
import { createStore } from 'redux'

function todos(state = [], action) {
  switch (action.type) {
    case 'ADD_TODO':
      return state.concat([action.text])
    default:
      //createStore를 실행 했을때 최초로 한번 reducer를 실행시킵니다.
      //createStore의 두번째 인자를 주고싶지 않다면 이곳에서 최초의
      //reducer state를 반환해줘야 합니다.
      return state
  }
}

let store = createStore(todos, ['Use Redux'])

store.dispatch({
  type: 'ADD_TODO',
  text: 'Read the docs'
})

console.log(store.getState())
// [ 'Use Redux', 'Read the docs' ]
```

