---
id: english-error-messages
category: English
difficulty: junior
daily: true
---

# Как читать английские сообщения об ошибках?

## Ответ

Типичные фразы в ошибках и их значение:

| Фраза | Перевод |
|---|---|
| `is not defined` | переменная не объявлена |
| `cannot read properties of undefined` | обращение к свойству у `undefined` |
| `is not a function` | значение не является функцией |
| `unexpected token` | синтаксическая ошибка в коде |
| `failed to fetch` | ошибка сетевого запроса |
| `CORS error` | запрос заблокирован политикой браузера |
| `404 Not Found` | ресурс не найден на сервере |

```js
// "Cannot read properties of null (reading 'id')"
// Значит: user равен null, а мы пытаемся прочитать user.id
const user = null;
console.log(user.id); // ошибка — нужна проверка перед обращением
```
