---
id: http-headers
category: Backend
difficulty: junior
daily: true
---

# Какие HTTP заголовки используются чаще всего?

## Ответ

Заголовки передают метаданные запроса и ответа: тип контента, авторизацию, кэширование, CORS.

```http
# Запрос
GET /api/users HTTP/1.1
Host: api.example.com
Authorization: Bearer eyJhbGc...
Content-Type: application/json
Accept: application/json

# Ответ
HTTP/1.1 200 OK
Content-Type: application/json
Cache-Control: max-age=3600
Access-Control-Allow-Origin: https://myapp.com
```

| Заголовок | Назначение |
|---|---|
| `Content-Type` | Формат тела запроса/ответа |
| `Authorization` | Токен аутентификации (Bearer, Basic) |
| `Accept` | Какой формат ответа ожидает клиент |
| `Cache-Control` | Правила кэширования (`no-cache`, `max-age`) |
| `Access-Control-Allow-Origin` | Разрешение CORS для домена |
| `Cookie` / `Set-Cookie` | Передача и установка куки |
