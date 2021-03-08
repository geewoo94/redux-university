# combineReducers

## `combineReducers(reducers)`

앱이 커질수록 한 가지 reducer로 모든 상태를 다 관리하기는 역부족입니다.

reducer 하나당 관련있는 상태들끼리 모아두고 redcuer를 결합해 rootReducer를 만들어 봅시다.

```javascript
import { combineReducers, createStore } from 'redux'
import todos from './todos'
import counter from './counter'

const rootReducer = combineReducers({
  todos,
  counter
})

const store = createStore(rootReducer)
```

`combineReducers`는 인자로 **객체**를 받는다. 그 후에 `store.getState().todos` or `store.getState().counter` 를 통해 상태에 접근할 수 있다. 

combineReducers를 사용한다면 createStore의 두번째 인자 preloadedState는 결합된 형태의 최초 상태로 정의해 줘야 합니다.

```javascript
const store = createStore(rootReducer, {
    todos: //...,
    counter: //...
})
```

reducer안에서 이 기본 값을 정의했다면 preloadedState는 생략 가능합니다. 

> #### combineReducers를 사용한다면 reducer는 아래 규칙을 지켜야만 합니다.

* 식별되지 않은 모든 상태에 대해서는 첫 인수로 주어진 `state`를 그대로 반환해야 합니다.
* `undefined`를 반환해서는 안 됩니다. 이 `return`문에서 쉽게 할 수 있는 실수로, 다른 곳에서 에러가 나기 전에 `combineReducers`에서 에러를 발생\(throw\)시킵니다.
* `state`가 `undefined`로 주어지면 반드시 해당 리듀서의 초기 상태를 반환해야 합니다. 예전 룰을 따르면 초기 상태 또한 `undefined`가 될 수 없습니다. ES6의 선택적 인수\(optional arguments\) 문법을 사용하면 간편하지만, 직접 첫 인수가 `undefined`가 아닌지 확인할 수도 있습니다.

