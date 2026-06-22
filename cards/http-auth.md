---
id: http-auth
category: Backend
daily: true
---
# Как работает HTTP-аутентификация?
## Ответ
Аутентификация в HTTP передаётся через заголовок `Authorization`. Основные схемы:

```http
# Bearer Token (JWT, OAuth 2.0) — самый распространённый
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiYWxpY2UifQ...

# Basic Auth — логин:пароль в base64 (только с HTTPS!)
Authorization: Basic dXNlcjpwYXNzd29yZA==

# API Key в заголовке
X-API-Key: my-secret-key-12345
```

Коды ответов:
- `401 Unauthorized` — токен отсутствует или невалиден
- `403 Forbidden` — токен валиден, но прав недостаточно

Bearer токен проверяется сервером при каждом запросе. Храните его в `httpOnly cookie` или `localStorage` (с учётом XSS-рисков).
