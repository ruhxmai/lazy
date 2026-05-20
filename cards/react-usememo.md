---
id: react-usememo
category: Frontend
difficulty: junior
daily: true
---

# Для чего нужны useMemo и useCallback?

## Ответ

Оба хука предотвращают лишние вычисления и ре-рендеры за счёт мемоизации.

```js
import { useMemo, useCallback } from 'react';

// useMemo — кэширует результат вычисления
const total = useMemo(() => {
  return items.reduce((sum, item) => sum + item.price, 0);
}, [items]); // пересчитывается только при изменении items

// useCallback — кэширует саму функцию
const handleClick = useCallback(() => {
  console.log(id);
}, [id]); // новая функция создаётся только при изменении id
```

- `useMemo` → возвращает **значение**
- `useCallback` → возвращает **функцию**
- Без мемоизации при каждом ре-рендере создаётся новый объект/функция
- Применяй только при реальных проблемах с производительностью — преждевременная оптимизация усложняет код
