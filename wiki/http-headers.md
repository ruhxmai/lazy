---
title: HTTP Headers
category: Backend
---

# HTTP Заголовки

HTTP-заголовки (headers) — метаданные, передаваемые вместе с запросом или ответом. Они сообщают серверу и клиенту дополнительную информацию: тип контента, авторизацию, настройки кеширования и многое другое.

## Заголовки запроса (Request Headers)

Отправляются клиентом (браузером, мобильным приложением, `fetch`):

| Заголовок | Пример | Назначение |
|-----------|--------|------------|
| `Content-Type` | `application/json` | Тип тела запроса |
| `Authorization` | `Bearer <token>` | Авторизация |
| `Accept` | `application/json` | Что клиент хочет получить |
| `Cookie` | `sessionId=abc123` | Отправка куки |
| `User-Agent` | `Mozilla/5.0...` | Информация о браузере |

## Заголовки ответа (Response Headers)

Отправляются сервером:

| Заголовок | Пример | Назначение |
|-----------|--------|------------|
| `Content-Type` | `application/json; charset=utf-8` | Тип тела ответа |
| `Set-Cookie` | `token=xyz; HttpOnly` | Установка куки |
| `Cache-Control` | `no-cache`, `max-age=3600` | Управление кешем |
| `Access-Control-Allow-Origin` | `*` | CORS — кому разрешён доступ |
| `Location` | `/new-url` | Редирект (при 301/302) |

## Схема

```mermaid
sequenceDiagram
  participant B as Browser
  participant S as Server

  B->>S: POST /api/login
  Note over B,S: Content-Type: application/json
  Note over B,S: Accept: application/json
  Note over B,S: Body: {"email":"...","password":"..."}

  S-->>B: 200 OK
  Note over S,B: Content-Type: application/json
  Note over S,B: Set-Cookie: token=abc; HttpOnly
  Note over S,B: Body: {"user": {...}}
```

## Content-Type и форматы тела

```http
# Отправка JSON
POST /api/users HTTP/1.1
Content-Type: application/json

{"name": "Alice", "age": 25}

# Отправка HTML-формы
POST /login HTTP/1.1
Content-Type: application/x-www-form-urlencoded

username=alice&password=secret

# Загрузка файла
POST /upload HTTP/1.1
Content-Type: multipart/form-data; boundary=----boundary
```

## CORS и заголовки безопасности

CORS (Cross-Origin Resource Sharing) — механизм, позволяющий браузеру делать запросы на другой домен.

```
Frontend (localhost:3000) → запрос → API (localhost:8080)

Браузер автоматически добавляет:
  Origin: http://localhost:3000

Сервер должен ответить:
  Access-Control-Allow-Origin: http://localhost:3000
```

Без `Access-Control-Allow-Origin` браузер **заблокирует ответ** — но запрос до сервера дойдёт!

## Авторизация через заголовок

```js
fetch('/api/profile', {
  headers: {
    'Authorization': `Bearer ${token}`,
    'Content-Type': 'application/json'
  }
});
```

## Карточки

- Для чего нужен заголовок `Content-Type`?
- Как браузер узнаёт, что сервер разрешает CORS-запрос?
- Чем отличается `Cookie` от `Set-Cookie`?
- Как передать JWT-токен в HTTP-запросе?
- Что делает заголовок `Cache-Control: no-cache`?
