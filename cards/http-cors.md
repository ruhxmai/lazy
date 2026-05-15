---
id: http-cors
category: Backend
daily: true
---
# Что такое CORS и почему браузер блокирует запросы?
## Ответ
CORS (Cross-Origin Resource Sharing) — механизм безопасности браузера. Браузер блокирует запросы к другому origin (иной домен, протокол или порт), если сервер явно не разрешил их.

Сервер разрешает запросы нужным заголовком:
```http
Access-Control-Allow-Origin: https://myapp.com
```

**Preflight-запрос:** перед «сложными» запросами (PUT, DELETE, кастомные заголовки) браузер отправляет `OPTIONS`, чтобы уточнить разрешения:
```http
OPTIONS /api/data HTTP/1.1
Origin: https://myapp.com
Access-Control-Request-Method: POST
Access-Control-Request-Headers: Content-Type
```

Сервер отвечает:
```http
Access-Control-Allow-Origin: https://myapp.com
Access-Control-Allow-Methods: GET, POST, PUT
Access-Control-Allow-Headers: Content-Type
```

**Важно:** CORS — защита браузера. `curl` и Postman его не проверяют.
