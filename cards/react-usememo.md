---
id: react-usememo
category: Frontend
daily: true
---
# Зачем нужен хук useMemo в React?
## Ответ
`useMemo` кэширует результат вычисления между рендерами. Пересчёт происходит только при изменении зависимостей.

```js
const sortedList = useMemo(() => {
  return [...items].sort((a, b) => a.name.localeCompare(b.name));
}, [items]);
```

Используй когда вычисление дорогостоящее. Отличие от `useCallback`: `useMemo` кэширует **значение**, `useCallback` — **функцию**.
