---
id: react-usecallback
category: Frontend
difficulty: junior
daily: true
---

# Для чего нужен хук useCallback?

## Ответ

`useCallback` мемоизирует функцию — возвращает ту же ссылку на функцию между рендерами, если зависимости не изменились.

```jsx
import { useCallback, useState } from 'react';

function Parent() {
  const [count, setCount] = useState(0);

  // Без useCallback — новая функция при каждом рендере Parent
  // const handleClick = () => console.log('clicked');

  // С useCallback — та же функция, пока count не изменится
  const handleClick = useCallback(() => {
    console.log('count:', count);
  }, [count]);

  return <Child onClick={handleClick} />;
}

// React.memo предотвращает лишний рендер Child, если props не изменились
const Child = React.memo(({ onClick }) => {
  return <button onClick={onClick}>Click</button>;
});
```

- Полезен только в паре с `React.memo` или как зависимость в `useEffect`/`useCallback` дочерних компонентов
- Бездумно оборачивать каждую функцию в `useCallback` — избыточно и замедляет код
