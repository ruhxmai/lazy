---
id: sql-null
category: Backend
daily: true
---
# Как работает NULL в SQL?
## Ответ
`NULL` означает отсутствие значения. Сравнение с `NULL` через `=` всегда возвращает `UNKNOWN`, поэтому используй `IS NULL` / `IS NOT NULL`.

```sql
-- Неправильно — вернёт 0 строк:
SELECT * FROM users WHERE email = NULL;

-- Правильно:
SELECT * FROM users WHERE email IS NULL;
SELECT * FROM users WHERE email IS NOT NULL;

-- COALESCE возвращает первое НЕ-NULL значение:
SELECT COALESCE(phone, 'не указан') AS phone FROM users;

-- COUNT(*) считает все строки, COUNT(col) игнорирует NULL:
SELECT COUNT(*), COUNT(email) FROM users;
```

`NULL` не равен даже самому себе: `NULL = NULL` → `UNKNOWN`.
