---
id: http-headers
category: Backend
difficulty: junior
daily: true
---

# Какие HTTP-заголовки должен знать каждый разработчик?

## Ответ

**Заголовки запроса:**

```http
POST /api/users HTTP/1.1
Content-Type: application/json       <- тип тела запроса
Authorization: Bearer eyJhbGc...     <- токен аутентификации
Accept: application/json             <- что хотим получить в ответ
```

**Заголовки ответа:**

```http
HTTP/1.1 200 OK
Content-Type: application/json
Cache-Control: max-age=3600          <- кеш на 1 час
Access-Control-Allow-Origin: *       <- CORS: разрешить все источники
```

**Шпаргалка:**

| Заголовок | Для чего |
|---|---|
| `Content-Type` | Тип тела (`application/json`, `text/html`) |
| `Authorization` | Аутентификация (`Bearer`, `Basic`) |
| `Cache-Control` | Управление кешем |
| `Access-Control-Allow-Origin` | CORS политика |
| `Accept` | Ожидаемый формат ответа |
