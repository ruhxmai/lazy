---
id: http-authentication
category: Backend
difficulty: junior
daily: true
---

# Чем отличаются Basic Auth, JWT и Cookie-сессии?

## Ответ

Три основных способа аутентификации в HTTP:

**Basic Auth** — логин:пароль в Base64 в заголовке `Authorization`. Легко декодируется, безопасно только по HTTPS.
```http
Authorization: Basic dXNlcjpwYXNzd29yZA==
```

**Bearer / JWT** — токен, полученный при логине, stateless (сервер его не хранит, только проверяет подпись).
```http
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
```

**Cookie / Session** — сервер хранит сессию, клиенту отдаёт `session_id` в cookie, браузер отправляет его автоматически.
```http
Set-Cookie: session_id=abc123; HttpOnly; Secure; SameSite=Strict
```

**Ключевое отличие:** JWT — stateless (не нужен shared storage, но токен нельзя отозвать до истечения `exp`), сессии — stateful (нужен Redis/БД, но можно мгновенно разлогинить пользователя).

Не путайте **Authentication** (кто ты) и **Authorization** (что тебе разрешено) — это разные этапы.
