---
id: react-memo
category: Frontend
difficulty: junior
daily: true
---

# Что делает React.memo и чем отличается от useMemo?

## Ответ

`React.memo` — HOC, который оборачивает **компонент** и пропускает его ре-рендер, если пропсы не изменились (shallow compare).

`useMemo` — хук, который кэширует **результат вычисления** внутри компонента.

```jsx
// Без React.memo — кнопка ре-рендерится при каждом обновлении родителя
function Button({ label }) {
  return <button>{label}</button>;
}

// С React.memo — ре-рендерится только при изменении label
const Button = React.memo(function Button({ label }) {
  return <button>{label}</button>;
});

// useMemo — кэширует вычисление, не компонент
function List({ items }) {
  const sorted = useMemo(
    () => [...items].sort(),
    [items] // пересчитает только если items изменился
  );
  return <ul>{sorted.map(i => <li key={i}>{i}</li>)}</ul>;
}
```

- `React.memo` — мемоизирует **компонент** (пропускает рендер)
- `useMemo` — мемоизирует **значение** (пропускает вычисление)
- Применяй только когда есть реальная проблема производительности
