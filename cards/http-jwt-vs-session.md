---
id: http-jwt-vs-session
category: Backend
difficulty: junior
daily: true
---

# Чем JWT-аутентификация отличается от сессионной (session-based)?

## Ответ

**Session-based:** сервер хранит состояние сессии (в памяти или БД), клиенту выдаётся `session_id` в cookie.

```http
Set-Cookie: session_id=abc123; HttpOnly
```
Сервер при каждом запросе ищет сессию по `session_id` в своём хранилище.

**JWT (JSON Web Token):** сервер ничего не хранит — вся информация (payload) закодирована прямо в токене и подписана секретным ключом.

```http
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

| | Session | JWT |
|---|---|---|
| Хранение | На сервере | На клиенте (в токене) |
| Масштабирование | Сложнее (нужен shared store) | Проще (stateless) |
| Отзыв доступа | Мгновенный (удалить сессию) | Сложный (нужен blacklist) |
| Размер запроса | Маленький (только id) | Больше (весь payload) |

> JWT удобен для микросервисов и API без сохранения состояния, но отозвать скомпрометированный токен до истечения срока действия — отдельная проблема.
