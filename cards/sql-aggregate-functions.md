---
id: sql-aggregate-functions
category: Backend
daily: true
---
# Что такое агрегатные функции SQL?
## Ответ
Агрегатные функции вычисляют **одно значение** из набора строк. Используются вместе с `GROUP BY`.

```sql
SELECT
  COUNT(*)           AS total_rows,      -- все строки включая NULL
  COUNT(email)       AS rows_with_email, -- игнорирует NULL
  SUM(amount)        AS total_amount,
  AVG(amount)        AS avg_amount,
  MIN(created_at)    AS first_order,
  MAX(created_at)    AS last_order
FROM orders
WHERE status = 'completed';

-- Группировка по пользователю
SELECT
  user_id,
  COUNT(*)   AS order_count,
  SUM(amount) AS total_spent
FROM orders
GROUP BY user_id
HAVING SUM(amount) > 1000;
```

> `WHERE` фильтрует строки **до** агрегации.  
> `HAVING` фильтрует **после** агрегации (работает с агрегатными функциями).
