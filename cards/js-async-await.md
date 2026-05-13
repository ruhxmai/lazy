---
id: js-async-await
category: Frontend
difficulty: junior
daily: true
---

# Чем async/await отличается от .then()/.catch()?

## Ответ

`async/await` — синтаксический сахар над промисами. Код выглядит синхронным, но остаётся асинхронным.

```js
// Промисы
fetch('/api/user')
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));

// async/await
async function getUser() {
  try {
    const res = await fetch('/api/user');
    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}
```

- `await` приостанавливает выполнение функции до разрешения промиса
- Ошибки ловятся через `try/catch`
- Функция с `async` всегда возвращает промис
