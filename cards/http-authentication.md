---
id: http-authentication
category: Backend
daily: true
---
# Как работает Bearer Token аутентификация?
## Ответ
BearerToken — клиент отправляет токен (обычно JWT) в заголовке `Authorization` при каждом запросе. Сервер проверяет токен без хранения состояния сессии (stateless).

Схема:
1. Клиент `POST /login` с логином/паролем → сервер возвращает токен
2. Клиент сохраняет токен (localStorage / httpOnly cookie)
3. Каждый запрос — `Authorization: Bearer <token>`
4. Сервер верифицирует подпись и срок действия

```http
POST /login
Content-Type: application/json
{ "email": "user@example.com", "password": "secret" }

→ 200 OK
{ "token": "eyJhbGciOiJIUzI1NiJ9..." }

GET /profile
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
```
