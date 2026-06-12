---
id: react-usememo
category: Frontend
daily: true
---
# Зачем нужен useMemo и чем он отличается от useCallback?
## Ответ
`useMemo` мемоизирует **значение** (результат вычисления), `useCallback` — **функцию**. Оба пересчитываются только при изменении зависимостей.

```js
// useMemo — дорогое вычисление
const sortedItems = useMemo(() => {
  return [...items].sort((a, b) => a.price - b.price);
}, [items]);

// useCallback — стабильная ссылка на функцию
const handleClick = useCallback(() => {
  doSomething(id);
}, [id]);
```

Используй `useMemo` только для действительно тяжёлых вычислений — лишняя мемоизация добавляет накладные расходы и усложняет код.
