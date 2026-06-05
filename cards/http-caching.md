---
id: http-caching
category: Backend
daily: true
---
# Как работает HTTP-кэширование?
## Ответ
Браузер и прокси-серверы сохраняют копии ответов, чтобы не делать повторные запросы к серверу.

Ключевые заголовки:
```http
Cache-Control: max-age=3600   # кэш действителен 1 час
Cache-Control: no-cache       # всегда проверять у сервера (revalidate)
Cache-Control: no-store       # не кэшировать совсем
ETag: "v1-abc123"             # токен версии ресурса
Last-Modified: Thu, 05 Jun 2025 10:00:00 GMT
```

Алгоритм проверки:
1. Браузер смотрит: есть ли кэш и не истёк ли `max-age`?
2. Если истёк — шлёт `If-None-Match: "v1-abc123"` или `If-Modified-Since`
3. Сервер отвечает `304 Not Modified` (без тела) или новым ресурсом `200 OK`
