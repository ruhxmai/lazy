---
id: react-memo
category: React
daily: true
---
# Чем отличается React.memo от useMemo?

## Ответ
- **`React.memo`** — HOC, который мемоизирует **компонент** целиком. Предотвращает повторный рендер, если пропсы не изменились.
- **`useMemo`** — хук, который мемоизирует **результат вычисления** внутри компонента.

```jsx
// React.memo — оборачивает компонент
const MyList = React.memo(({ items }) => {
  return <ul>{items.map(i => <li key={i}>{i}</li>)}</ul>;
});

// useMemo — мемоизирует дорогое вычисление
function Parent({ data }) {
  const sorted = useMemo(
    () => [...data].sort(),
    [data] // пересчитывается только при изменении data
  );
  return <MyList items={sorted} />;
}
```

Используй `React.memo`, когда компонент рендерится часто, но пропсы редко меняются. `useMemo` — когда вычисление дорогое.
