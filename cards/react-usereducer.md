---
id: react-usereducer
category: Frontend
difficulty: junior
daily: true
---

# Когда использовать useReducer вместо useState?

## Ответ

`useReducer` лучше `useState`, когда:
- Состояние — объект с несколькими взаимосвязанными полями
- Следующее состояние зависит от предыдущего
- Логика обновления сложная или ветвящаяся

```js
const initialState = { count: 0, step: 1 };

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { ...state, count: state.count + state.step };
    case "setStep":
      return { ...state, step: action.payload };
    case "reset":
      return initialState;
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <>
      <p>Счёт: {state.count}</p>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "reset" })}>Сброс</button>
    </>
  );
}
```
