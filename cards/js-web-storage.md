---
id: js-web-storage
category: Frontend
daily: true
---
# Чем отличаются `localStorage`, `sessionStorage` и `cookie`?

## Ответ

Все три хранят данные на клиенте, но по-разному:

| | `localStorage` | `sessionStorage` | `cookie` |
|---|---|---|---|
| Время жизни | Пока не удалят вручную | До закрытия вкладки | Задаётся `expires`/`max-age` |
| Объём | ~5-10 МБ | ~5-10 МБ | ~4 КБ |
| Отправляется на сервер | Нет | Нет | Да, в каждом HTTP-запросе |
| Доступ из JS | `localStorage.getItem()` | `sessionStorage.getItem()` | `document.cookie` (если не `HttpOnly`) |

```js
// localStorage — переживает перезагрузку и закрытие браузера
localStorage.setItem('theme', 'dark');
localStorage.getItem('theme'); // 'dark'

// sessionStorage — живёт только в рамках одной вкладки
sessionStorage.setItem('formDraft', JSON.stringify({ name: 'Alex' }));

// cookie — единственный вариант, который сервер видит сам
document.cookie = 'session_id=abc123; max-age=3600; Secure';
```

**Частая ошибка junior-разработчиков:** хранить JWT-токен в `localStorage` — он доступен любому JS-коду на странице, включая внедрённый через XSS. Для чувствительных токенов безопаснее `HttpOnly` cookie, которую JavaScript вообще не может прочитать.
