---
id: http-cors
category: Backend
difficulty: junior
daily: true
---

# Что такое CORS и почему браузер блокирует запросы?

## Ответ

CORS (Cross-Origin Resource Sharing) — механизм браузера, блокирующий запросы с одного домена к другому без явного разрешения сервера.

```
https://myapp.com → запрос к https://api.other.com
☓ Браузер блокирует (разные origins)
```

Сервер разрешает доступ через заголовки ответа:

```http
Access-Control-Allow-Origin: https://myapp.com
Access-Control-Allow-Methods: GET, POST, PUT
Access-Control-Allow-Headers: Content-Type, Authorization
```

Настройка на Express:

```js
const cors = require('cors');
app.use(cors({ origin: 'https://myapp.com' }));
```

- Блокирует только браузер — curl и Postman CORS не проверяют
- Перед сложными запросами браузер шлёт preflight (OPTIONS)
- `Access-Control-Allow-Origin: *` разрешает доступ всем
