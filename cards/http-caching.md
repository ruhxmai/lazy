---
id: http-caching
category: Backend
daily: true
---
# Как работает HTTP-кэширование?
## Ответ
Браузер сохраняет ответы и повторно использует их. Управляется заголовками:

```
Cache-Control: max-age=3600   # кэш на 1 час
Cache-Control: no-cache       # проверять у сервера каждый раз
Cache-Control: no-store       # не кэшировать вообще
ETag: "abc123"                # версия ресурса
If-None-Match: "abc123"       # браузер спрашивает: изменилось?
```

Если ресурс не изменился — сервер отвечает `304 Not Modified` без тела ответа.
