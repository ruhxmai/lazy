---
id: sql-keys
category: Backend
difficulty: junior
daily: true
---

# Чем отличается PRIMARY KEY от FOREIGN KEY?

## Ответ

**PRIMARY KEY** — уникальный идентификатор строки в своей таблице. Не может быть NULL, только один на таблицу (может быть составным).

```sql
CREATE TABLE users (
  id INT PRIMARY KEY,
  name VARCHAR(100)
);
```

**FOREIGN KEY** — ссылка на PRIMARY KEY другой таблицы, обеспечивает целостность связи.

```sql
CREATE TABLE orders (
  id INT PRIMARY KEY,
  user_id INT,
  FOREIGN KEY (user_id) REFERENCES users(id)
);
```

Без FOREIGN KEY можно вставить `user_id`, которого нет в `users` — база это не проверит. С FOREIGN KEY такая вставка вызовет ошибку.
