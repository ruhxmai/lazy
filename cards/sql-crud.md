---
id: sql-crud
category: Backend
difficulty: junior
daily: true
---

# Как выглядят базовые CRUD-операции в SQL?

## Ответ

CRUD — Create, Read, Update, Delete. Четыре базовые операции с данными в любой БД.

```sql
-- Create
INSERT INTO users (name, email)
VALUES ('Alice', 'alice@example.com');

-- Read
SELECT id, name FROM users
WHERE active = true;

-- Update
UPDATE users
SET name = 'Bob'
WHERE id = 1;

-- Delete
DELETE FROM users
WHERE id = 1;
```

- `INSERT INTO` — создание новой записи
- `SELECT ... FROM ... WHERE` — чтение с условием
- `UPDATE ... SET ... WHERE` — обновление (WHERE обязателен, иначе обновятся **все** строки!)
- `DELETE FROM ... WHERE` — удаление (без WHERE удалит **всю** таблицу!)
