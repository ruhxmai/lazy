---
id: sql-null-handling
category: Backend
difficulty: junior
daily: true
---

# Почему `WHERE column = NULL` никогда не работает в SQL?

## Ответ

`NULL` означает «неизвестное значение». Любое сравнение с `NULL` через `=` или `!=` даёт `NULL` (а не `true`/`false`), поэтому строка не попадёт в результат.

```sql
-- ❌ Никогда ничего не вернёт, даже если email действительно NULL
SELECT * FROM users WHERE email = NULL;

-- ✅ Правильно
SELECT * FROM users WHERE email IS NULL;
SELECT * FROM users WHERE email IS NOT NULL;
```

**Полезные функции для работы с NULL:**

```sql
-- Подставить значение по умолчанию, если NULL
SELECT COALESCE(nickname, name, 'Anonymous') FROM users;

-- Проверить конкретное поле
SELECT NULLIF(discount, 0) FROM orders; -- вернёт NULL, если discount = 0
```

**Ловушка с агрегатными функциями:** `COUNT(column)` игнорирует `NULL`, а `COUNT(*)` считает все строки:

```sql
SELECT COUNT(*), COUNT(phone) FROM users;
-- COUNT(*) = 100, COUNT(phone) = 82 — у 18 пользователей phone IS NULL
```

**Ловушка с IN:** `NOT IN` со списком, содержащим `NULL`, вернёт пустой результат.
