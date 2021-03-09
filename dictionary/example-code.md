# Example Code

## Reducer

```typescript
type action = { type: string, payload: number };

const counter = (state = 0, action) => {
    // state === store.getState()
    // action은 store.dispatch를 통해 전달된 action이다.
    switch (action.type) {
        case 'INCREASE':
            return action.payload
        case 'DECREASE':
            return action.payload
        default:
            //createStore를 실행 했을때 최초로 한번 reducer를 실행시킵니다.
            //createStore의 두번째 인자를 주고싶지 않다면 이곳에서 최초의
            //reducer state를 반환해줘야 합니다.
            return state
}
```

## asd

