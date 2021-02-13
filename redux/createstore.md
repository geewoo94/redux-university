# createStore

## createStore\(reducer, \[preloadedState\], \[enhancer\]\)

리덕스의 store를 생산한다. redux에서는 **하나의 store만** 사용하기를 **강력히 권장**하고 있다.

### [reducer](../dictionary/example-code.md#reducer)

reducing 함수이다. action handler를 통해 다음 상태트리를 반환한다.

### preloadedState

최초의 상태이다. 만약 combineReducers로 reducer를 만들었다면 그에 대응하는 최초의 상태를 정의해줘야 한다.

### enhancer

추가적인 third party를 사용할수 있다. redux에서 기본적으로 제공되는 인핸서는 applyMiddleware가 있다. 여러가지 enhancer를 사용하려면 compose를 사용하여 결합할수 있다.

#### 예

```typescript
import { createStore } from 'redux'

function todos(state = [], action) {
  switch (action.type) {
    case 'ADD_TODO':
      return state.concat([action.text])
    default:
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

