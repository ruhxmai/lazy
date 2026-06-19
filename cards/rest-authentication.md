---
id: rest-authentication
category: Backend
daily: true
---
# Как работает аутентификация в REST API через JWT?
## Ответ
**JWT (JSON Web Token)** — токен с подписью, который сервер выдаёт при логине, а клиент отправляет в каждом запросе.

```
1. POST /api/login  { email, password }
   ← { token: "eyJhbGc..." }

2. GET /api/profile
   Authorization: Bearer eyJhbGc...
```

Структура токена: `header.payload.signature`
- **Header** — алгоритм (HS256)
- **Payload** — данные пользователя (id, role, exp)
- **Signature** — подпись для проверки целостности

```javascript
// Декодировать payload (без верификации):
const payload = JSON.parse(atob(token.split('.')[1]));
console.log(payload.exp); // timestamp истечения
```

Токен **не шифруется** — не храни в нём пароли.
