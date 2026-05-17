---
id: react-usecallback
category: Frontend
daily: true
---

# Зачем нужен useCallback и когда его использовать?

## Ответ

`useCallback` возвращает мемоизированную версию функции — она пересоздаётся только при изменении зависимостей. Применяется, чтобы не ломать мемоизацию дочерних компонентов.

```jsx
import { useCallback, useState, memo } from 'react';

function Parent() {
  const [count, setCount] = useState(0);

  // без useCallback — новая функция при каждом рендере Parent
  // с useCallback — та же ссылка, пока не изменятся зависимости
  const handleClick = useCallback(() => {
    console.log('clicked');
  }, []); // [] — создаётся один раз

  return (
    <>
      <button onClick={() => setCount(c => c + 1)}>{count}</button>
      <Child onClick={handleClick} />
    </>
  );
}

const Child = memo(({ onClick }) => {
  console.log('Child render'); // не рендерится при изменении count
  return <button onClick={onClick}>Click</button>;
});
```

Применяй вместе с `React.memo` — иначе толку нет.
