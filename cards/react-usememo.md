---
id: react-usememo
category: Frontend
daily: true
---
# Для чего нужны useMemo и useCallback?

## Ответ

- `useMemo` — мемоизирует **результат** вычисления, пересчитывает только при изменении зависимостей
- `useCallback` — мемоизирует **функцию**, предотвращает её пересоздание при каждом рендере

```js
const total = useMemo(
  () => items.reduce((sum, i) => sum + i.price, 0),
  [items]
);

const handleClick = useCallback(() => {
  onSelect(id);
}, [id, onSelect]);
```

Используй только при реальных проблемах производительности — преждевременная оптимизация усложняет код.
