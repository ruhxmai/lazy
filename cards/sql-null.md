---
id: sql-null
category: Backend
difficulty: junior
daily: true
---

# Как работать с NULL в SQL?

## Ответ

`NULL` — отсутствие значения. С ним нельзя сравниваться через `=`, только через `IS NULL` / `IS NOT NULL`.

```sql
-- Неправильно (всегда возвращает 0 строк):
SELECT * FROM users WHERE email = NULL;

-- Правильно:
SELECT * FROM users WHERE email IS NULL;
SELECT * FROM users WHERE email IS NOT NULL;

-- COALESCE — первое не-NULL значение:
SELECT name, COALESCE(phone, 'не указан') AS phone FROM users;

-- NULLIF — возвращает NULL если значения равны:
SELECT NULLIF(score, 0) FROM results;  -- 0 становится NULL
```

- `NULL != NULL` — любое сравнение с NULL даёт `UNKNOWN`
- `COUNT(*)` считает все строки, `COUNT(column)` игнорирует NULL
- `GROUP BY` группирует все NULL вместе
