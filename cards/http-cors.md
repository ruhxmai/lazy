---
id: http-cors
category: Backend
daily: true
---

# Что такое CORS и почему браузер блокирует запросы?

## Ответ

CORS (Cross-Origin Resource Sharing) — политика безопасности браузера. Запрос к другому домену блокируется, если сервер явно не разрешил это через заголовок.

```
# Браузер добавляет к запросу:
Origin: https://mysite.com

# Сервер должен ответить:
Access-Control-Allow-Origin: https://mysite.com
```

```js
// Разрешить CORS в Express:
app.use((req, res, next) => {
  res.header('Access-Control-Allow-Origin', '*');
  res.header('Access-Control-Allow-Methods', 'GET,POST,PUT,DELETE');
  next();
});
```

Ошибка CORS — всегда проблема **сервера**, а не клиентского кода.
