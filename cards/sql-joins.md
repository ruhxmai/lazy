---
id: sql-joins
category: Backend
difficulty: junior
daily: false
---

# INNER JOIN vs LEFT JOIN в SQL?

## Ответ

**INNER JOIN** — только строки, которые есть в **обеих** таблицах:

```sql
SELECT users.name, orders.total
FROM users
INNER JOIN orders ON users.id = orders.user_id;
-- Пользователи БЕЗ заказов не попадут в результат
```

**LEFT JOIN** — все строки из левой таблицы + совпадения из правой (если нет — `NULL`):

```sql
SELECT users.name, orders.total
FROM users
LEFT JOIN orders ON users.id = orders.user_id;
-- Все пользователи, даже без заказов (total = NULL)
```
