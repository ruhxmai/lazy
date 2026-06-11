---
id: react-usememo
category: Frontend
difficulty: junior
daily: true
---

# Для чего нужен хук useMemo?

## Ответ

`useMemo` кэширует результат вычисления и пересчитывает его только при изменении зависимостей. Используется для оптимизации «дорогих» операций.

```js
import { useMemo } from 'react';

function ProductList({ products, filter }) {
  const filtered = useMemo(
    () => products.filter(p => p.name.includes(filter)),
    [products, filter] // пересчитать только если изменились
  );

  return <ul>{filtered.map(p => <li key={p.id}>{p.name}</li>)}</ul>;
}
```

- Без `useMemo` фильтрация запускалась бы при каждом ре-рендере
- Похож на `useCallback`, но кэширует **значение**, а не функцию
- Не использовать без необходимости: добавляет сложность и накладные расходы
