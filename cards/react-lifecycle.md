---
id: react-lifecycle
category: React
daily: true
---
# Как работает жизненный цикл компонента в React (функциональный)?
## Ответ
Функциональный компонент использует хук `useEffect` для управления жизненным циклом.

```jsx
import { useState, useEffect } from 'react';

function MyComponent({ userId }) {
  const [user, setUser] = useState(null);

  // Монтирование (componentDidMount)
  useEffect(() => {
    console.log('Mounted!');
  }, []);

  // Обновление при изменении userId (componentDidUpdate)
  useEffect(() => {
    fetch(`/api/users/${userId}`)
      .then(res => res.json())
      .then(setUser);

    // Размонтирование (componentWillUnmount)
    return () => {
      console.log('Cleanup!');
    };
  }, [userId]);

  return <div>{user?.name}</div>;
}
```

| Хук | Аналог в классе |
|---|---|
| `useEffect(fn, [])` | `componentDidMount` |
| `useEffect(fn, [x])` | `componentDidUpdate` |
| `return fn` внутри useEffect | `componentWillUnmount` |
| `React.memo` | `shouldComponentUpdate` |
