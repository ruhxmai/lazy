---
id: react-usememo
category: Frontend
daily: true
---
# Когда использовать useMemo и useCallback в React?
## Ответ
Оба хука нужны для **мемоизации** — кэширования между рендерами.

- **`useMemo`** — сохраняет результат вычисления (значение)
- **`useCallback`** — сохраняет саму функцию (не пересоздаёт при каждом рендере)

```js
const sortedList = useMemo(() => {
  return items.sort((a, b) => a - b);
}, [items]); // пересчитывается только при изменении items

const handleClick = useCallback(() => {
  console.log(id);
}, [id]); // пересоздаётся только при изменении id
```

Использовать только когда вычисление дорогое или функция передаётся в дочерний компонент с `React.memo`.
