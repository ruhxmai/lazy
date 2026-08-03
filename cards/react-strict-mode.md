---
id: react-strict-mode
category: Frontend
difficulty: junior
daily: true
---

# Почему в React.StrictMode эффекты и рендеры выполняются дважды?

## Ответ

`<React.StrictMode>` в dev-режиме **намеренно** вызывает рендер компонента и `useEffect` дважды подряд:

```jsx
<React.StrictMode>
  <App />
</React.StrictMode>
```

```js
useEffect(() => {
  console.log('mount'); // выведется дважды в dev
  return () => console.log('unmount');
}, []);
```

Это не баг — так React проверяет, что компонент **устойчив к повторному монтированию** (mount → unmount → mount). Если эффект ломается от повторного вызова, значит в коде спрятана проблема, которая проявится позже — например, при Suspense или будущих оптимизациях React.

Частые причины поломки:

```js
// ❌ Плохо: подписка без очистки — задвоится
useEffect(() => {
  socket.on('message', handleMessage);
}, []);

// ✅ Хорошо: cleanup возвращает подписку в исходное состояние
useEffect(() => {
  socket.on('message', handleMessage);
  return () => socket.off('message', handleMessage);
}, []);
```

Важно: **в production-сборке двойного вызова нет** — StrictMode влияет только на development.
