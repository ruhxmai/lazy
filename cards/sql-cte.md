---
id: sql-cte
category: Backend
daily: true
---

# Что такое CTE (Common Table Expressions) в SQL?

## Ответ

**CTE** — именованный временный результат запроса, объявляемый через `WITH` и существующий только во время выполнения одного запроса. Делает сложные запросы читаемыми — вместо вложенных подзапросов получаем последовательность именованных шагов.

```sql
WITH high_earners AS (
  SELECT id, name, salary
  FROM employees
  WHERE salary > 100000
)
SELECT department, COUNT(*)
FROM high_earners
JOIN departments USING (department_id)
GROUP BY department;
```

**Рекурсивный CTE** — позволяет обходить иерархические данные (дерево категорий, оргструктуру):

```sql
WITH RECURSIVE org_chart AS (
  SELECT id, name, manager_id, 1 AS level
  FROM employees
  WHERE manager_id IS NULL          -- анкор: топ-менеджер

  UNION ALL

  SELECT e.id, e.name, e.manager_id, oc.level + 1
  FROM employees e
  JOIN org_chart oc ON e.manager_id = oc.id  -- рекурсивная часть
)
SELECT * FROM org_chart ORDER BY level;
```

**CTE vs подзапрос:** результат тот же, но CTE читается сверху вниз как план запроса, а не вложенными скобками. В некоторых СУБД (Postgres) CTE может служить материализованной оптимизационной границей.
