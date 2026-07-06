---
id: sql-null
category: Backend
daily: true
---
# Почему `= NULL` не работает в SQL и как правильно сравнивать с NULL?

## Ответ

`NULL` означает «значение неизвестно», а не «пустое значение». Любое сравнение с `NULL` через `=` или `!=` возвращает `NULL` (не `TRUE` и не `FALSE`), поэтому строка отбрасывается из результата.

```sql
SELECT * FROM users WHERE deleted_at = NULL;   -- ❌ не вернёт строки с NULL, даже если они есть
SELECT * FROM users WHERE deleted_at != NULL;  -- ❌ тоже ничего не найдёт
```

**Правильно** — использовать `IS NULL` / `IS NOT NULL`:

```sql
SELECT * FROM users WHERE deleted_at IS NULL;      -- активные пользователи
SELECT * FROM users WHERE deleted_at IS NOT NULL;   -- удалённые
```

**Ловушка с `NOT IN`:** если подзапрос вернёт хотя бы один `NULL`, весь `NOT IN` перестаёт находить строки:

```sql
-- Если среди id есть NULL, запрос вернёт 0 строк
SELECT * FROM orders WHERE user_id NOT IN (SELECT id FROM banned_users);

-- Безопаснее — NOT EXISTS
SELECT * FROM orders o
WHERE NOT EXISTS (SELECT 1 FROM banned_users b WHERE b.id = o.user_id);
```

**Функции для работы с NULL:** `COALESCE(value, default)` возвращает первое не-NULL значение — удобно для замены NULL на дефолт при выводе.
