---
id: react-usereducer
category: Frontend
daily: true
---
# Когда использовать `useReducer` вместо `useState`?

## Ответ

`useReducer` подходит, когда состояние сложное: несколько связанных полей, следующее состояние зависит от предыдущего, или логика обновления разрослась в кучу `if`/`setState` подряд.

```js
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    case 'reset':
      return { count: 0 };
    default:
      throw new Error('Unknown action: ' + action.type);
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <>
      <p>{state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </>
  );
}
```

Вместо прямого вызова `setState` компонент вызывает `dispatch(action)`, а вся логика перехода состояний собрана в одной функции `reducer` — её легко тестировать отдельно от компонента.

**Признаки, что пора переходить с `useState` на `useReducer`:** много связанных `useState` для одного объекта, обновление зависит от предыдущего state сложным образом, нужно логировать/дебажить каждое изменение состояния.
