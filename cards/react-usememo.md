---
id: react-usememo
category: Frontend
daily: true
---
# Для чего нужен хук useMemo в React?
## Ответ
`useMemo` кэширует результат вычисления и пересчитывает его только при изменении зависимостей. Используется для оптимизации дорогих операций, чтобы избежать лишней работы при каждом рендере.

```js
import { useMemo } from 'react';

function ProductList({ items, filter }) {
  // filtered пересчитывается только когда items или filter меняются
  const filtered = useMemo(
    () => items.filter(item => item.name.includes(filter)),
    [items, filter]
  );

  return <ul>{filtered.map(i => <li key={i.id}>{i.name}</li>)}</ul>;
}
```

**Когда применять:** вычисление занимает заметное время (сортировка/фильтрация большого массива, сложные расчёты).  
**Не злоупотребляй:** `useMemo` сам имеет накладные расходы и делает код сложнее.
