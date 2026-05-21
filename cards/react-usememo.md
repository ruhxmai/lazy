---
id: react-usememo
category: React
daily: true
---
# Чем useMemo отличается от useCallback?
## Ответ
Оба хука кешируют вычисления, чтобы избежать лишних перерасчётов при ре-рендере.

- **`useMemo`** — кеширует **результат** вычисления (значение)
- **`useCallback`** — кеширует **саму функцию** (ссылку на неё)

```js
// useMemo: возвращает вычисленное значение
const total = useMemo(() => items.reduce((s, i) => s + i.price, 0), [items]);

// useCallback: возвращает стабильную ссылку на функцию
const handleClick = useCallback(() => {
  console.log(id);
}, [id]);
```

Используй `useCallback`, когда передаёшь функцию в дочерний компонент, обёрнутый в `React.memo`.
