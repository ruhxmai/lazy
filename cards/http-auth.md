---
id: http-auth
category: HTTP
daily: true
---
# Как работает авторизация по JWT в HTTP?

## Ответ
JWT (JSON Web Token) — токен, который передаётся в заголовке `Authorization` при каждом запросе.

**Процесс:**
1. Клиент отправляет логин/пароль → сервер выдаёт JWT
2. Клиент сохраняет токен (обычно в памяти или `localStorage`)
3. При каждом запросе клиент добавляет заголовок:

```http
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

4. Сервер проверяет подпись токена и извлекает данные пользователя

```js
const response = await fetch('/api/profile', {
  headers: {
    Authorization: `Bearer ${token}`
  }
});
```

JWT состоит из трёх частей: `header.payload.signature`. Сервер не хранит токены — только секретный ключ для проверки подписи.
