---
id: http-cors
category: Backend
difficulty: junior
daily: true
---

# Что такое CORS и почему браузер блокирует запросы?

## Ответ

**CORS** (Cross-Origin Resource Sharing) — механизм, который разрешает или запрещает браузеру делать запросы к **другому домену, порту или протоколу**.

Браузер блокирует кросс-доменные запросы по умолчанию — это политика **Same-Origin Policy**.

```http
# Браузер сначала шлёт preflight-запрос OPTIONS:
OPTIONS /api/data HTTP/1.1
Origin: https://my-app.com

# Сервер должен ответить разрешающими заголовками:
Access-Control-Allow-Origin: https://my-app.com
Access-Control-Allow-Methods: GET, POST, PUT
Access-Control-Allow-Headers: Content-Type
```

**Частые ситуации:**
- `Access-Control-Allow-Origin: *` — разрешить всем (не работает с credentials)
- Без CORS-заголовков на сервере — браузер заблокирует ответ

> CORS — это проверка **браузера**. Запросы сервер→сервер (например, из Node.js) не ограничены CORS.
