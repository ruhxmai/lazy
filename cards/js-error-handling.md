---
id: js-error-handling
category: JavaScript
daily: true
---
# Как работает обработка ошибок в JavaScript?
## Ответ
Используй `try / catch / finally` и `throw` для управления ошибками.

```js
function divide(a, b) {
  if (b === 0) throw new Error('Division by zero');
  return a / b;
}

try {
  console.log(divide(10, 0));
} catch (err) {
  console.error(err.message); // 'Division by zero'
} finally {
  console.log('Выполняется всегда');
}
```

- `try` — блок, который может выбросить ошибку
- `catch(err)` — перехватывает ошибку; `err.message` и `err.stack` доступны
- `finally` — выполняется всегда, даже при ошибке
- `throw` — вручную выбрасывает любое значение (обычно `new Error(...)`)
