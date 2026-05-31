---
id: http-cors
category: Backend
daily: true
---
# Что такое CORS и как он работает?
## Ответ
**CORS** (Cross-Origin Resource Sharing) — механизм безопасности браузера. Он блокирует запросы к другому домену/порту/протоколу, если сервер явно не разрешает их через заголовки ответа.

Браузер добавляет заголовок `Origin`, сервер отвечает:
```
Access-Control-Allow-Origin: https://myapp.com
Access-Control-Allow-Methods: GET, POST, PUT
Access-Control-Allow-Headers: Content-Type, Authorization
```

Для «сложных» запросов (PUT, DELETE, кастомные заголовки) браузер сначала делает **preflight** (`OPTIONS`).

```js
// Node.js / Express
app.use(cors({ origin: 'https://myapp.com' }));
```

CORS — это только браузерная защита; curl/Postman его не проверяют.
