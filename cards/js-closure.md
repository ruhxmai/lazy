---
id: js-closure
category: Frontend
difficulty: junior
daily: true
---

# Что такое замыкание (closure)?

## Ответ

Функция, которая **запоминает переменные** из внешней области видимости даже после её завершения.

```js
function counter() {
  let n = 0;
  return () => ++n;
}
const c = counter();
c(); // 1
c(); // 2
```

Переменная `n` живёт внутри замыкания — снаружи не доступна, но функция её помнит.
