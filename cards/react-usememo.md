---
id: react-usememo
category: React
daily: true
---
# Для чего нужен хук useMemo?
## Ответ
`useMemo` кеширует результат вычисления и пересчитывает его только при изменении зависимостей. Используй для дорогих операций, чтобы не повторять их при каждом рендере.

```js
import { useMemo } from 'react';

function ProductList({ products, filterText }) {
  const filtered = useMemo(() => {
    return products.filter(p =>
      p.name.toLowerCase().includes(filterText.toLowerCase())
    );
  }, [products, filterText]);

  return filtered.map(p => <div key={p.id}>{p.name}</div>);
}
```

Отличие от `useCallback`: `useMemo` кеширует **значение**, `useCallback` — **функцию**.

Не злоупотребляй: для простых вычислений `useMemo` добавляет лишний overhead.
