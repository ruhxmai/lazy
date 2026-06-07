---
id: rest-auth
category: Backend
difficulty: junior
daily: true
---

# Как работает JWT-аутентификация в REST API?

## Ответ

JWT (JSON Web Token) — токен из трёх частей (header.payload.signature) в base64. Клиент получает его при логине и отправляет в каждом запросе в заголовке `Authorization`.

```
// Структура токена:
eyJhbGciOiJIUzI1NiJ9    ← header  (алгоритм подписи)
.eyJ1c2VySWQiOjF9        ← payload (данные: userId, role, exp)
.SflKxwRJSMeKKF2QT4fw   ← signature (HMAC-подпись)
```

```js
// Запрос с токеном:
fetch("/api/profile", {
  headers: { Authorization: `Bearer ${token}` }
});

// Проверка на сервере (Node.js):
const jwt = require("jsonwebtoken");
const payload = jwt.verify(token, process.env.JWT_SECRET);
```

- Токен **stateless** — сервер не хранит сессии
- Не храни JWT в `localStorage` (уязвим к XSS) — используй `httpOnly` cookie
- Access token живёт ~15 мин, refresh token — 7–30 дней
