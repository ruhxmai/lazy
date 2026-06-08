---
id: react-memo
category: Frontend
difficulty: junior
daily: true
---

# Зачем нужен React.memo?

## Ответ

`React.memo` — HOC, который **пропускает перерендер** компонента, если его props не изменились (поверхностное сравнение).

```jsx
const Button = React.memo(({ onClick, label }) => {
  console.log('render');
  return <button onClick={onClick}>{label}</button>;
});

// Если label и onClick не изменились — компонент не перерендерится
// Оборачивай функции-пропсы в useCallback, иначе они всегда новые:
const handleClick = useCallback(() => doSomething(), []);
```

Не применяй `React.memo` везде — мемоизация сама по себе стоит памяти. Использует её там, где перерендер дорогой или очень частый.
