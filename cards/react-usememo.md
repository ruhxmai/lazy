---
id: react-usememo
category: React
difficulty: junior
daily: true
---

# Что делает useMemo и когда его использовать?

## Ответ

`useMemo` кэширует результат вычисления между рендерами. Пересчёт происходит только если изменились зависимости.

```js
import { useMemo } from "react";

function ProductList({ products, filter }) {
  const filtered = useMemo(
    () => products.filter(p => p.category === filter),
    [products, filter]
  );

  return filtered.map(p => <div key={p.id}>{p.name}</div>);
}
```

- Используй когда вычисление **дорогое**: сортировка больших массивов, сложные расчёты
- Не нужен для простых операций — добавляет лишние расходы
- Отличие от `useCallback`: `useMemo` кэширует **значение**, `useCallback` — **функцию**
- Зависимости работают так же, как в `useEffect`
