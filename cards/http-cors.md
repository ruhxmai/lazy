---
id: http-cors
category: Backend
daily: true
---
# Что такое CORS и почему браузер блокирует запросы?
## Ответ
**CORS** (Cross-Origin Resource Sharing) — механизм безопасности браузера, запрещающий запросы с одного origin на другой, если сервер явно не разрешает это.

**Origin** = протокол + хост + порт. Если хоть одно отличается — origin другой.

Сервер разрешает cross-origin запросы через заголовки ответа:
```http
Access-Control-Allow-Origin: https://myapp.com
Access-Control-Allow-Methods: GET, POST, PUT
Access-Control-Allow-Headers: Content-Type, Authorization
```

Перед «опасным» запросом браузер отправляет **preflight** (метод `OPTIONS`). Только при ответе `200` с нужными заголовками отправляется сам запрос.
