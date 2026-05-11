---
id: http-status-codes
category: Backend
daily: true
---

# Что означают группы HTTP-кодов 2xx, 3xx, 4xx, 5xx?

## Ответ

| Группа | Смысл | Частые коды |
|--------|-------|-------------|
| 2xx | Успех | 200 OK, 201 Created, 204 No Content |
| 3xx | Перенаправление | 301 Moved Permanently, 304 Not Modified |
| 4xx | Ошибка клиента | 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found |
| 5xx | Ошибка сервера | 500 Internal Server Error, 502 Bad Gateway, 503 Unavailable |

Правило: **4xx = виноват клиент** (неверный запрос), **5xx = виноват сервер** (упал или перегружен).
