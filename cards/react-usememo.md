---
id: react-usememo
category: Frontend
daily: true
---
# Для чего нужен хук useMemo в React?

## Ответ

`useMemo` **запоминает результат вычисления** и пересчитывает его только при изменении зависимостей. Используется для оптимизации дорогих операций.

```jsx
import { useMemo } from 'react';

function ProductList({ products, filterText }) {
  const filtered = useMemo(() => {
    return products.filter(p => p.name.includes(filterText));
  }, [products, filterText]); // пересчёт только при изменении этих значений

  return filtered.map(p => <div key={p.id}>{p.name}</div>);
}
```

**Когда использовать:**
- Тяжёлые вычисления (сортировка/фильтрация больших массивов)
- Стабильная ссылка на объект для передачи в `React.memo`-компонент

**Когда НЕ использовать:** для простых операций — overhead от useMemo дороже самого вычисления.
