---
id: http-headers
category: Backend
daily: true
---
# Какие HTTP-заголовки должен знать каждый разработчик?

## Ответ

Заголовки передают метаданные запроса и ответа.

```
// Заголовки запроса (Request)
Content-Type: application/json       // формат тела запроса
Authorization: Bearer <token>        // токен авторизации
Accept: application/json             // ожидаемый формат ответа
Origin: https://myapp.com            // источник (для CORS)

// Заголовки ответа (Response)
Content-Type: application/json       // формат ответа
Cache-Control: max-age=3600          // правила кэширования
Access-Control-Allow-Origin: *       // разрешить CORS
Set-Cookie: session=abc; HttpOnly    // установить cookie
```

**CORS** — браузер блокирует запросы на чужой домен, если сервер не вернул `Access-Control-Allow-Origin`. Это защита, а не баг.
