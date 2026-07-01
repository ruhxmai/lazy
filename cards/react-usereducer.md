---
id: react-usereducer
category: Frontend
difficulty: junior
daily: true
---

# Когда использовать useReducer вместо useState?

## Ответ

`useReducer` удобен, когда **состояние сложное** (много полей) или новое состояние **зависит от предыдущего** через понятные действия (actions).

```jsx
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'reset':
      return { count: 0 };
    default:
      throw new Error('Unknown action');
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <>
      <button onClick={() => dispatch({ type: 'increment' })}>+1</button>
      <button onClick={() => dispatch({ type: 'reset' })}>Сброс</button>
      <p>{state.count}</p>
    </>
  );
}
```

Плюсы: вся логика обновлений в одном месте, легче тестировать, удобнее для сложных форм и связанных полей состояния.
