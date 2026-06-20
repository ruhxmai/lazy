---
id: http-auth
category: Backend
daily: true
---
# Как работает аутентификация в HTTP-запросах?
## Ответ
Аутентификация — подтверждение личности клиента. Три основных подхода:

```http
# Basic Auth — логин:пароль в base64 (только через HTTPS!)
Authorization: Basic dXNlcjpwYXNzd29yZA==

# Bearer Token — JWT или другой токен
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...

# Session Cookie — сервер выдаёт идентификатор сессии
Set-Cookie: sessionId=abc123; HttpOnly; Secure; SameSite=Strict
```

- **Basic** — прост, но небезопасен без TLS
- **JWT/Bearer** — stateless: данные в токене, сервер ничего не хранит
- **Session** — stateful: данные на сервере, клиент хранит только ID
- **401 Unauthorized** — не аутентифицирован; **403 Forbidden** — нет прав
