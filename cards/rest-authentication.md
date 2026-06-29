---
id: rest-authentication
category: Backend
difficulty: junior
daily: true
---

# Как работает JWT-аутентификация в REST API?

## Ответ

**JWT (JSON Web Token)** — токен из трёх частей, разделённых точкой: `header.payload.signature`.

**Flow:**
1. Клиент отправляет логин/пароль → сервер возвращает JWT
2. Клиент сохраняет токен и отправляет его в каждом запросе
3. Сервер проверяет подпись и читает данные без обращения к БД

```js
// Клиент: отправка токена в заголовке
fetch('/api/profile', {
  headers: { 'Authorization': `Bearer ${token}` }
});

// Сервер (Node.js + jsonwebtoken)
const jwt = require('jsonwebtoken');

// Создание токена
const token = jwt.sign({ userId: 123 }, SECRET_KEY, { expiresIn: '1h' });

// Проверка токена
const payload = jwt.verify(token, SECRET_KEY);
console.log(payload.userId); // 123
```

**Преимущества:** stateless, масштабируем, данные хранятся в токене.  
**Минус:** токен нельзя инвалидировать до истечения срока без blacklist.
