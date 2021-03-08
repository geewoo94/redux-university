# Example Code

## Reducer

```typescript
type action = { type: string, payload: number };
type state = number;

const counter = (state = 0, action) => {
    // state === store.getState()
    // action은 store.dispatch를 통해 전달된 action이다.
    switch (action.type) {
        case 'INCREASE':
            return action.payload
        case 'DECREASE':
            return action.payload
        default:
            return state
}
```

## asd

