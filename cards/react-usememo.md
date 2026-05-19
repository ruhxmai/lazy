---
id: react-usememo
category: Frontend
daily: true
---
# В чём разница между useMemo и useCallback?

## Ответ
**`useMemo`** кэширует **результат вычисления** — пересчитывает только при изменении зависимостей.  
**`useCallback`** кэширует **саму функцию** — не даёт ей пересоздаваться при каждом рендере.

```js
// useMemo — мемоизация значения
const sorted = useMemo(() => {
  return [...items].sort((a, b) => a - b);
}, [items]);

// useCallback — мемоизация функции
const handleClick = useCallback(() => {
  console.log(id);
}, [id]);
```

Полезны когда дочерний компонент обёрнут в `React.memo` — предотвращают лишние рендеры.
