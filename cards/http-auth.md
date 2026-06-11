---
id: http-auth
category: Backend
difficulty: junior
daily: true
---

# Как работает Bearer-аутентификация в HTTP?

## Ответ

Bearer-токен (обычно JWT) передаётся в заголовке `Authorization`. Сервер проверяет его подпись и предоставляет или отклоняет доступ.

```http
GET /api/profile HTTP/1.1
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

```js
// Отправка токена на клиенте
fetch('/api/profile', {
  headers: {
    Authorization: `Bearer ${token}`
  }
});
```

- **Basic** — `логин:пароль` в base64, небезопасно без HTTPS
- **Bearer** — токен (JWT), сервер проверяет без сессии (stateless)
- **JWT** состоит из трёх частей: `header.payload.signature`
- Токен обычно хранят в `httpOnly cookie` (безопаснее) или `localStorage`
