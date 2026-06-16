---
title: HTTP Аутентификация
category: Backend
---
# HTTP Аутентификация

Аутентификация (authentication) — процесс проверки **кто** делает запрос к серверу. Авторизация (authorization) — проверка **что** этому пользователю разрешено делать. Это разные понятия!

## Основные подходы

### Session + Cookie
Сервер создаёт сессию в базе данных и выдаёт клиенту `session_id` через cookie. При каждом запросе браузер автоматически отправляет cookie.

**Плюсы:** легко инвалидировать сессию. **Минусы:** плохо масштабируется (нужно хранить сессии на сервере).

### Basic Auth
Логин и пароль передаются в заголовке `Authorization`, закодированные в Base64. Безопасно только по HTTPS.

```
Authorization: Basic dXNlcjpwYXNzd29yZA==
```

### JWT (JSON Web Token)
Сервер выдаёт подписанный токен с данными пользователя. Клиент хранит его (обычно в cookie или localStorage) и передаёт в заголовке `Authorization: Bearer`.

JWT состоит из трёх частей: `header.payload.signature`, разделённых точками.

```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

**Плюсы:** stateless, отлично масштабируется. **Минусы:** нельзя отозвать до истечения срока.

## Схема

```mermaid
sequenceDiagram
    participant C as Client
    participant S as Server
    participant DB as Database

    Note over C,S: Шаг 1 — Вход
    C->>S: POST /login {email, password}
    S->>DB: Проверить учётные данные
    DB-->>S: OK, user found
    S-->>C: 200 {token: "eyJ..."}

    Note over C,S: Шаг 2 — Защищённый запрос
    C->>S: GET /profile<br/>Authorization: Bearer eyJ...
    S->>S: Проверить подпись JWT
    S-->>C: 200 {user data}

    Note over C,S: Шаг 3 — Выход (JWT)
    C->>C: Удалить токен на клиенте
```

## Сравнение подходов

| Метод | Состояние на сервере | Масштабируемость | Отзыв токена |
|-------|---------------------|-----------------|---------------|
| Session/Cookie | Да (в БД) | Средняя | Легко |
| Basic Auth | Нет | Отличная | Только смена пароля |
| JWT | Нет | Отличная | Сложно (нужен blacklist) |

## Карточки
- Чем аутентификация отличается от авторизации?
- Из чего состоит JWT-токен?
- Почему JWT сложно отозвать?
- Что такое Bearer token?
- Чем Session/Cookie хуже JWT при масштабировании?
