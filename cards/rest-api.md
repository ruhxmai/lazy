---
id: rest-api
category: Backend
difficulty: junior
daily: true
---

# Что такое REST API?

## Ответ

Архитектурный стиль для построения API. Основные принципы:

- **Stateless** — сервер не хранит состояние клиента между запросами
- **Ресурсы по URL** — `/users`, `/posts/42`
- **HTTP методы** — `GET` получить, `POST` создать, `PUT` обновить, `DELETE` удалить
- **JSON** как стандартный формат данных

```
GET    /users       → список пользователей
POST   /users       → создать пользователя
GET    /users/1     → пользователь с id=1
DELETE /users/1     → удалить пользователя
```
