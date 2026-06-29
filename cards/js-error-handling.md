---
id: js-error-handling
category: JavaScript
difficulty: junior
daily: true
---

# Как работает try/catch/finally в JavaScript?

## Ответ

**`try`** — блок кода, который может выбросить ошибку.  
**`catch`** — перехватывает ошибку, получает объект `Error`.  
**`finally`** — выполняется всегда, независимо от результата.

```js
try {
  const data = JSON.parse('invalid json');
} catch (err) {
  console.log(err.name);    // SyntaxError
  console.log(err.message); // Unexpected token ...
} finally {
  console.log('Всегда выполняется');
}
```

**Типы ошибок:** `Error`, `TypeError`, `ReferenceError`, `SyntaxError`, `RangeError`.

Можно выбросить свою ошибку через `throw`:

```js
function divide(a, b) {
  if (b === 0) throw new Error('Деление на ноль!');
  return a / b;
}

try {
  divide(10, 0);
} catch (err) {
  console.log(err.message); // 'Деление на ноль!'
}
```

В `async/await` ошибки из `await` также ловятся через `try/catch`.
