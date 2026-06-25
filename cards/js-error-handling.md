---
id: js-error-handling
category: Frontend
daily: true
---
# Как работает try/catch/finally в JavaScript?
## Ответ
Блок `try` выполняется, если возникает ошибка — управление передаётся в `catch`. `finally` выполняется всегда, независимо от наличия ошибки.

```js
try {
  const data = JSON.parse(invalidJson); // throws SyntaxError
} catch (err) {
  console.error(err.name, err.message); // SyntaxError ...
} finally {
  console.log('done'); // always runs
}
```

Основные типы ошибок: `Error`, `TypeError`, `ReferenceError`, `SyntaxError`, `RangeError`. Можно создать свой класс через `class MyError extends Error`.
