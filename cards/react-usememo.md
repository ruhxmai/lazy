---
id: react-usememo
category: Frontend
daily: true
---
# Чем отличаются useMemo и useCallback?
## Ответ
Оба хука мемоизируют результат, чтобы не пересчитывать его при каждом рендере.

- **useMemo** — кэширует **значение** (результат вызова функции).
- **useCallback** — кэширует **саму функцию** (её ссылку).

```js
// Пересчитывается только при изменении list
const sorted = useMemo(() => [...list].sort(), [list]);

// Новая функция создаётся только при изменении id
const handleClick = useCallback(() => {
  fetchItem(id);
}, [id]);
```

Применяй, когда вычисление дорогое или передаёшь функцию в `React.memo`-компонент.
