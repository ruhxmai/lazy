---
id: sql-null
category: Backend
daily: true
---
# Как правильно работать с NULL в SQL?
## Ответ
`NULL` — отсутствие значения. Сравнивать через `=` нельзя — нужно `IS NULL` / `IS NOT NULL`.

Полезные функции:
- `COALESCE(a, b, ...)` — первое не-NULL значение
- `NULLIF(a, b)` — NULL если `a = b`, иначе `a` (защита от деления на ноль)
- `IS NULL` / `IS NOT NULL` — единственный способ проверить NULL

```sql
-- Wrong: всегда возвращает пустой результат
SELECT * FROM users WHERE email = NULL;

-- Correct
SELECT * FROM users WHERE email IS NULL;

-- Заменить NULL значением по умолчанию
SELECT COALESCE(phone, 'N/A') FROM users;

-- Защита от деления на ноль
SELECT total / NULLIF(count, 0) FROM stats;
```
