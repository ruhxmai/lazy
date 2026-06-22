---
id: sql-cte
category: Backend
daily: true
---
# Что такое CTE в SQL (оператор WITH)?
## Ответ
CTE (Common Table Expression) — именованный временный результат запроса, объявляемый через `WITH`. Делает сложные запросы читаемее и позволяет ссылаться на результат несколько раз.

```sql
WITH active_users AS (
  SELECT id, name FROM users WHERE active = true
),
user_orders AS (
  SELECT user_id, COUNT(*) AS total
  FROM orders
  GROUP BY user_id
)
SELECT u.name, o.total
FROM active_users u
JOIN user_orders o ON u.id = o.user_id
ORDER BY o.total DESC;
```

Рекурсивные CTE (`WITH RECURSIVE`) позволяют обходить иерархические данные: деревья, графы.

```sql
WITH RECURSIVE subordinates AS (
  SELECT id, name, manager_id FROM employees WHERE id = 1
  UNION ALL
  SELECT e.id, e.name, e.manager_id
  FROM employees e
  JOIN subordinates s ON e.manager_id = s.id
)
SELECT * FROM subordinates;
```
