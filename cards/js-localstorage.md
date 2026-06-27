---
id: js-localstorage
category: Frontend
daily: true
---
# Чем отличается localStorage от sessionStorage?
## Ответ
Оба хранят данные в браузере в виде строк (key-value), но отличаются временем жизни:

| | localStorage | sessionStorage |
|---|---|---|
| Время жизни | Навсегда | До закрытия вкладки |
| Объём | ~5 МБ | ~5 МБ |
| Общий между вкладками | Да | Нет |

```js
localStorage.setItem('token', 'abc123')
const token = localStorage.getItem('token')
localStorage.removeItem('token')
localStorage.clear()
```

> Не храни sensitive-данные (пароли, JWT) — localStorage доступен через JS (XSS-риск).
