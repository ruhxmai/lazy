---
id: sql-null
category: Backend
daily: true
---
# Как работает NULL в SQL и почему NULL != NULL?

## Ответ

`NULL` означает **отсутствие значения**. Любое сравнение с NULL возвращает `UNKNOWN`, а не `TRUE` или `FALSE`.

- `NULL = NULL` → UNKNOWN (поэтому `WHERE col = NULL` ничего не вернёт!)
- Проверяй через `IS NULL` / `IS NOT NULL`
- Агрегатные функции `SUM`, `AVG`, `COUNT(col)` игнорируют NULL
- `COUNT(*)` считает все строки, включая строки с NULL
- `COALESCE(a, b)` — возвращает первое не-NULL значение

```sql
-- Неправильно:
SELECT * FROM users WHERE phone = NULL;   -- пустой результат!

-- Правильно:
SELECT * FROM users WHERE phone IS NULL;

-- Заменить NULL значением по умолчанию:
SELECT COALESCE(phone, 'не указан') AS phone FROM users;
```
