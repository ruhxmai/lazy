---
id: react-useref
category: React
daily: true
---
# Для чего используется useRef в React?
## Ответ
`useRef` возвращает объект `{ current: value }`, который сохраняется между рендерами и **не вызывает** перерисовку при изменении.

Два основных применения:
1. Прямой доступ к DOM-элементу
2. Хранение мутабельных значений (таймеры, предыдущие значения)

```jsx
import { useRef, useEffect } from 'react';

function App() {
  const inputRef = useRef(null);
  const countRef = useRef(0); // не вызывает ре-рендер

  useEffect(() => {
    inputRef.current.focus(); // доступ к DOM
  }, []);

  function handleClick() {
    countRef.current += 1; // мутируем без ре-рендера
    console.log('Clicks:', countRef.current);
  }

  return <input ref={inputRef} onClick={handleClick} />;
}
```
