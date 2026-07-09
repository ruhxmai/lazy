---
id: http-authentication
category: Backend
daily: true
---

# Как работает Bearer-аутентификация с JWT?

## Ответ

Клиент один раз логинится (`POST /login`), получает **JWT-токен** и дальше отправляет его в заголовке `Authorization` при **каждом** запросе. Сервер не хранит сессию — он **stateless**: просто проверяет подпись токена.

```http
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjQyfQ.4f8a...
```

JWT состоит из трёх частей через точку: `header.payload.signature`

- **header** — алгоритм подписи (`HS256`, `RS256`)
- **payload** — данные пользователя: `userId`, `role`, `exp` (время истечения)
- **signature** — HMAC/RSA-подпись сервера секретным ключом

```js
// payload легко прочитать (Base64), но НЕЛЬЗЯ подделать без секрета сервера
const payload = JSON.parse(atob(token.split('.')[1]));
// { userId: 42, role: 'user', exp: 1735689600 }
```

**Важно:** payload **не зашифрован**, а только закодирован — не кладите туда пароли или другие секреты. Подделать токен без знания серверного ключа нельзя: любое изменение payload ломает signature.

**Где хранить токен на клиенте:**

| Место | Риск |
|---|---|
| `localStorage` | уязвим к XSS — вредоносный скрипт может украсть токен |
| Память (переменная в JS) | безопаснее, но теряется при перезагрузке страницы |
| HttpOnly cookie | недоступен для JS (защита от XSS), но нужна защита от CSRF |

**Рекомендация для SPA:** access-токен — в памяти, refresh-токен — в `HttpOnly` cookie.
