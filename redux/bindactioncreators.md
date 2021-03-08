# bindActionCreators

## `bindActionCreators(actionCreators, dispatch)`

reducer가 많아지면 [combineReducers](combinereducers.md)로 하나로 합칠수가 있었습니다. redux는 마찬가지로 actionCreator를 하나로 합칠수 있는 간단한 헬퍼 함수도 지원합니다.

### bindActionCreators는 다음과 같이 사용 할 수 있습니다.

```typescript
import store from './store'

type ActionCreator = (payload?: any) => ({ type: string, payload })

const actionA = (payload) => ({ type: 'actionA', payload })
const actionB = (payload) => ({ type: 'actionB', payload })

const boundActions = bindActionCreators(
    {
        actionA,
        actionB
    },
    store.dispatch
)

// 이후에 boundActions.actionA()와 같은 형식으로 dispatch없이 사용할수 있다.
// dispatch(actionA())를 실행시킨것과 같다. WOW~
```

### 왜 사용할까요?

리액트를 사용한다고 가정했을때 우리는 하위컴포넌트에게 dispatch라는 함수를 알려주기 싫을수도 있습니다. 또 JSX문법을 사용한다면 간단하게 모든 action을 하위 컴포넌트에게 전달 할수도 있구요.

```jsx
const boundActions = bindActionCreators(
    {
        actionA,
        actionB
    },
    store.dispatch
)

<Component {...boundActions} />
```

