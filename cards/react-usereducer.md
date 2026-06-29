---
id: react-usereducer
category: Frontend
difficulty: junior
daily: true
---

# Когда использовать useReducer вместо useState?

## Ответ

`useReducer` — хук для управления сложным состоянием через функцию-редьюсер. Принимает `(reducer, initialState)`, возвращает `[state, dispatch]`.

```js
const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment': return { count: state.count + 1 };
    case 'decrement': return { count: state.count - 1 };
    case 'reset':     return initialState;
    default:          return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      <p>{state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
      <button onClick={() => dispatch({ type: 'reset' })}>Reset</button>
    </>
  );
}
```

**Когда useReducer лучше useState:**
- Много связанных полей состояния
- Следующее состояние зависит от текущего
- Сложная логика обновлений (несколько action-типов)
