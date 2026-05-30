---
id: react-usememo
category: Frontend
daily: true
---

# Для чего нужен хук `useMemo`?

## Ответ

`useMemo` **кэширует результат вычисления** и пересчитывает его только при изменении зависимостей. Используется для оптимизации тяжёлых операций.

```js
const sorted = useMemo(() => {
  return [...items].sort((a, b) => a.price - b.price);
}, [items]);
```

Без `useMemo` — сортировка при **каждом рендере**.
С `useMemo` — только при изменении `items`.

Отличие от `useCallback`: `useMemo` кэширует **значение**, `useCallback` — **функцию**.
