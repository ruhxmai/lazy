---
id: sql-cte
category: Backend
daily: true
---
# Что такое CTE (Common Table Expression) в SQL?
## Ответ
CTE — именованный временный результат запроса, определённый через `WITH`. Делает сложные запросы читаемее и позволяет переиспользовать подзапросы без дублирования.

```sql
WITH active_users AS (
  SELECT id, name FROM users WHERE active = true
),
orders_count AS (
  SELECT user_id, COUNT(*) AS cnt FROM orders GROUP BY user_id
)
SELECT u.name, o.cnt
FROM active_users u
JOIN orders_count o ON u.id = o.user_id;
```

Рекурсивный CTE (`WITH RECURSIVE`) позволяет обходить иерархические структуры: деревья, категории с подкатегориями.
