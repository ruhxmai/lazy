---
id: react-usestate
category: Frontend
daily: true
---

# Как работает useState и почему нельзя мутировать состояние напрямую?

## Ответ

`useState` возвращает пару: текущее значение и функцию-сеттер.

```js
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

React сравнивает **ссылки**. Прямая мутация не создаёт новую ссылку → ре-рендера не будет.

```js
// Массив — создавайте новый
setItems([...items, newItem]);  // ✅
items.push(newItem);            // ❌

// Объект — используйте spread
setUser({ ...user, name: 'Alex' }); // ✅
user.name = 'Alex';                 // ❌
```
