---
id: react-usereducer
category: Frontend
daily: true
---
# Когда использовать useReducer вместо useState?
## Ответ
`useReducer` подходит, когда состояние сложное (несколько взаимосвязанных полей) или следующее значение зависит от предыдущего. Логика обновления вынесена в чистую функцию-редьюсер.

```js
const reducer = (state, action) => {
  switch (action.type) {
    case 'increment': return { count: state.count + 1 };
    case 'reset':     return { count: 0 };
    default:          return state;
  }
};

const [state, dispatch] = useReducer(reducer, { count: 0 });
dispatch({ type: 'increment' });
```

`useState` — для простых независимых значений. `useReducer` — для конечных автоматов и сложной логики переходов.
