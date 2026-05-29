---
id: react-usememo
category: React
daily: true
---
# Для чего нужен хук useMemo в React?

## Ответ

`useMemo` мемоизирует результат вычисления и пересчитывает его только при изменении зависимостей. Используется для дорогих операций, чтобы не запускать их заново при каждом рендере.

```jsx
import { useMemo } from 'react';

function List({ items, filter }) {
  const filtered = useMemo(
    () => items.filter(i => i.includes(filter)),
    [items, filter] // пересчитать только если изменилось
  );

  return <ul>{filtered.map(i => <li key={i}>{i}</li>)}</ul>;
}
```

Не стоит злоупотреблять: для простых вычислений накладные расходы на мемоизацию перевешивают пользу. Разница с `useCallback`: `useMemo` кэширует **значение**, `useCallback` — **функцию**.
