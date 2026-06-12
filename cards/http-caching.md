---
id: http-caching
category: Backend
daily: true
---
# Как работает HTTP-кэширование?
## Ответ
Сервер передаёт заголовки, указывающие браузеру сколько хранить ответ:

```http
Cache-Control: max-age=3600    # кэш на 1 час
Cache-Control: no-cache        # всегда проверять свежесть
Cache-Control: no-store        # не кэшировать вообще
ETag: "abc123"                 # хэш версии ресурса
Last-Modified: Wed, 11 Jun 2026 12:00:00 GMT
```

При повторном запросе браузер шлёт `If-None-Match: "abc123"` — сервер вернёт **304 Not Modified** (без тела), если ресурс не изменился. Это экономит трафик.
