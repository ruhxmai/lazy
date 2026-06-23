---
title: HTTP Authentication
category: Backend
---

# HTTP-аутентификация

Аутентификация (Authentication) — процесс проверки личности: *кто* делает запрос. Не путать с авторизацией (Authorization) — *что* этому пользователю разрешено.

В HTTP существует три популярных подхода: Basic Auth, Bearer/JWT и Cookie-сессии.

## Basic Auth

Логин и пароль кодируются в Base64 и передаются в заголовке `Authorization`. Безопасно **только по HTTPS** — Base64 легко декодируется.

```http
Authorization: Basic dXNlcjpwYXNzd29yZA==
```

Применяется для внутренних API, CLI-утилит и простых сервисов.

## Bearer / JWT

Наиболее распространённый подход для SPA и мобильных приложений. Клиент получает токен при логине и отправляет его в каждом запросе.

```http
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

**JWT (JSON Web Token)** состоит из трёх частей, разделённых точкой:

```
header.payload.signature
```

- `header` — алгоритм подписи (`HS256`, `RS256`)
- `payload` — данные: `userId`, `roles`, `exp` (срок действия)
- `signature` — HMAC-подпись сервера; без секретного ключа подделать нельзя

Сервер **не хранит** токен — он stateless: просто проверяет подпись.

## Cookie / Session

Сервер создаёт сессию в хранилище (БД, Redis), отдаёт клиенту `session_id` в cookie. Браузер автоматически отправляет cookie в каждом запросе.

```http
Set-Cookie: session_id=abc123; HttpOnly; Secure; SameSite=Strict
```

- `HttpOnly` — JavaScript не может прочитать cookie (защита от XSS)
- `Secure` — только по HTTPS
- `SameSite=Strict` — защита от CSRF-атак

## Схема

```mermaid
sequenceDiagram
    participant Браузер
    participant Сервер
    participant БД

    Браузер->>Сервер: POST /login {email, password}
    Сервер->>БД: Найти пользователя, проверить пароль
    БД-->>Сервер: OK, user = {id: 42, role: "admin"}
    Сервер-->>Браузер: 200 { token: "eyJ..." }

    Браузер->>Сервер: GET /profile\nAuthorization: Bearer eyJ...
    Сервер->>Сервер: Проверить подпись JWT
    Сервер-->>Браузер: 200 { id: 42, name: "Alex" }

    Браузер->>Сервер: DELETE /admin/users/1\nAuthorization: Bearer eyJ...
    Сервер->>Сервер: JWT валиден, но role != "superadmin"
    Сервер-->>Браузер: 403 Forbidden
```

## Сравнение подходов

| Метод | Где хранить на клиенте | Stateless | Уязвимость |
|---|---|---|---|
| Basic Auth | нигде (каждый раз вводить) | да | перехват без HTTPS |
| JWT / Bearer | `localStorage` или memory | да | XSS (если в localStorage) |
| Cookie/Session | cookie (автоматически) | нет (нужен shared store) | CSRF |

**Рекомендация для SPA:** JWT в памяти (не localStorage) + refresh token в HttpOnly cookie.

## Карточки

- Как передаётся JWT-токен в HTTP-запросе?
- Чем аутентификация отличается от авторизации?
- Что находится в payload JWT и можно ли его подделать?
- Почему Basic Auth небезопасен без HTTPS?
- Что делают флаги `HttpOnly` и `SameSite` у cookie?
