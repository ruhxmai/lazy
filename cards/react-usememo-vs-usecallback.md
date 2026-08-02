---
id: react-usememo-vs-usecallback
category: Frontend
difficulty: junior
daily: true
---

# В чём разница между `useMemo` и `useCallback`?

## Ответ

Оба хука кэшируют значение между рендерами, но кэшируют **разное**:

- **`useMemo`** — кэширует **результат вычисления** (любое значение)
- **`useCallback`** — кэширует саму **функцию** (это частный случай `useMemo`)

```jsx
// useMemo — кэшируем вычисленное значение
const sortedList = useMemo(() => {
  return items.slice().sort((a, b) => a.price - b.price);
}, [items]);

// useCallback — кэшируем функцию-колбэк
const handleClick = useCallback(() => {
  onSelect(item.id);
}, [item.id, onSelect]);

// useCallback(fn, deps) эквивалентен useMemo(() => fn, deps)
```

Оба нужны, чтобы не создавать новую ссылку на каждый рендер — это важно при передаче пропсов в `React.memo`-компоненты или в массив зависимостей других хуков.
