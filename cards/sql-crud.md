---
id: sql-crud
category: Backend
daily: true
---
# Как выглядят базовые CRUD-операции в SQL?
## Ответ
CRUD — Create, Read, Update, Delete:

```sql
-- Create
INSERT INTO users (name, email)
VALUES ('Alice', 'alice@example.com');

-- Read
SELECT id, name FROM users WHERE active = true;

-- Update
UPDATE users SET name = 'Bob' WHERE id = 1;

-- Delete
DELETE FROM users WHERE id = 1;
```

`DELETE` без `WHERE` удаляет **все** строки таблицы. Для полной очистки быстрее использовать `TRUNCATE users;` — он не логирует каждую строку.
