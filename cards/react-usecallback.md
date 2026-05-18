---
id: react-usecallback
category: Frontend
daily: true
---

# Зачем нужны useCallback и useMemo в React?

## Ответ

`useMemo` — мемоизирует **результат** вычисления, пересчитывает только при изменении зависимостей.  
`useCallback` — мемоизирует **функцию**, предотвращает её пересоздание при каждом рендере.

```js
// useMemo — дорогое вычисление кешируется
const filtered = useMemo(
  () => items.filter(i => i.active),
  [items]
);

// useCallback — стабильная ссылка на функцию
const handleClick = useCallback(() => {
  doSomething(id);
}, [id]);

// Имеет смысл вместе с React.memo
const Child = React.memo(({ onClick }) => <button onClick={onClick} />);
```

Оба хука полезны только вместе с `React.memo` или как зависимости других хуков. Без этого — лишние затраты памяти.
