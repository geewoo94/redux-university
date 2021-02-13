# Example Code

## Reducer

```typescript
type action = { type: string, payload: number };
type state = number;

const counter = (state = 0, action) => {
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

