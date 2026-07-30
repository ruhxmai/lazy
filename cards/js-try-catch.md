---
id: js-try-catch
category: Frontend
difficulty: junior
daily: true
---

# Как обрабатывать ошибки в JavaScript с помощью try/catch?

## Ответ

`try/catch` перехватывает ошибки, которые возникают внутри блока `try`, не давая упасть всему приложению.

```js
try {
  const data = JSON.parse('{ invalid json');
} catch (error) {
  console.error('Не удалось распарсить:', error.message);
} finally {
  console.log('Выполнится в любом случае');
}
```

С `async/await` ошибки из отклонённых промисов тоже ловятся через `try/catch`:

```js
async function loadUser(id) {
  try {
    const res = await fetch(`/api/users/${id}`);
    if (!res.ok) throw new Error(`HTTP ${res.status}`);
    return await res.json();
  } catch (error) {
    console.error('Ошибка загрузки пользователя:', error);
    return null;
  }
}
```

**Важно:** `try/catch` не ловит ошибки в асинхронном коде без `await` (например, внутри `setTimeout` или необработанного `.then()`) — они улетают отдельно.

```js
try {
  setTimeout(() => { throw new Error('boom'); }, 0); // catch НЕ сработает
} catch (e) {
  // сюда не попадём
}
```

Свои ошибки удобно создавать через кастомные классы:

```js
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = 'ValidationError';
  }
}
```
