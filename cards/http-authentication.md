---
id: http-authentication
category: Backend
difficulty: junior
daily: true
---

# Как работает аутентификация в HTTP-запросах?

## Ответ

Аутентификация передаётся через заголовок `Authorization`:

| Тип | Формат | Применение |
|-----|--------|------------|
| Basic | `Basic base64(login:pass)` | Только по HTTPS, legacy |
| Bearer | `Bearer <token>` | JWT и OAuth 2.0 |
| API Key | `X-API-Key: <key>` | Простые сервисные API |

```js
// Bearer (JWT) — самый распространённый подход
fetch("/api/data", {
  headers: {
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIs...",
  },
});

// Где хранить токен?
// ✅ httpOnly cookie — защищает от XSS
// ⚠️  localStorage   — уязвим к XSS-атакам
```

JWT состоит из трёх частей: `header.payload.signature`, разделённых точкой.
