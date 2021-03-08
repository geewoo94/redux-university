# applyMiddleware

## `applyMiddleware(...middleware)`

store에 상태가 저장되기 전 또는 저장된 후에 특정한 작업을 하고싶다면 middleware를 사용할수 있습니다. applyMiddleware는 그런 middleware를 순서적으로 처리할수 있습니다. middleware는 다음과 같은 문법으로 작성 될 수 있습니다.

### middleware는 다음과 같이 구성됩니다.

```typescript
type MiddlewareAPI = { dispatch: Dispatch, getState: () => State }
type Middleware = (api: MiddlewareAPI) => (next: Dispatch) => Dispatch

const middleware: Middleware = api => next => action => {
    //api 에서는 store의 dispatch와 상태를 가져올수 있습니다.
    //next는 store의 dispatch와 같습니다.
    //action은 action creator를 통해 생성된 action입니다.
    
    //이곳에서 상태가 변경되기 전 무언갈 할 수 있습니다.
    
    next(action) //다음 미들웨어를 실행합니다.
    
    //이곳에서 상태가 변경된 후 무언갈 할 수 있습니다.
}
```

### applyMiddleware는 다음과 같이 사용 할 수 있습니다.

```typescript
import { createStore, applyMiddleware } from 'redux'
import { someMiddleware, anotherMiddleware } from './middlewares'
import rootReducer from './rootReducer'

const rootMiddleware = applyMiddleware(
    someMiddleware,
    anotherMiddleware
)

const store = createStore(
    rootReducer,
    preloadedState, // 생략 가
    rootMiddleware
)
```

대표적인 middleware로는 reduxThunk가 있습니다. 해당 middleware는 추후에 알아보도록 합시다.

