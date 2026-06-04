---
id: sql-crud
category: SQL
daily: true
---
# Какие SQL-операторы соответствуют CRUD-операциям?

## Ответ
CRUD — Create, Read, Update, Delete — базовые операции с данными.

```sql
-- Create (INSERT)
INSERT INTO users (name, email)
VALUES ('Alice', 'alice@example.com');

-- Read (SELECT)
SELECT id, name FROM users
WHERE email = 'alice@example.com';

-- Update (UPDATE)
UPDATE users
SET name = 'Alicia'
WHERE id = 1;

-- Delete (DELETE)
DELETE FROM users
WHERE id = 1;
```

**Важно:** всегда используй `WHERE` в `UPDATE` и `DELETE`, иначе изменятся/удалятся **все** строки таблицы.
