---
id: sql-having-vs-where
category: Backend
difficulty: junior
daily: true
---

# В чём разница между `WHERE` и `HAVING` в SQL?

## Ответ

**`WHERE`** фильтрует строки **до группировки** (`GROUP BY`) — работает с отдельными записями исходной таблицы. Нельзя использовать агрегатные функции (`COUNT`, `SUM` и т.д.).

**`HAVING`** фильтрует **группы после** `GROUP BY` — работает с результатом агрегации, поэтому в нём можно использовать `COUNT`, `SUM`, `AVG` и другие агрегатные функции.

```sql
SELECT department, COUNT(*) AS emp_count
FROM employees
WHERE status = 'active'        -- фильтр строк до группировки
GROUP BY department
HAVING COUNT(*) > 5;           -- фильтр групп после группировки
```

Порядок выполнения запроса: `FROM` → `WHERE` → `GROUP BY` → `HAVING` → `SELECT` → `ORDER BY`. Именно поэтому `WHERE` не видит агрегаты (они ещё не посчитаны), а `HAVING` не может фильтровать по столбцам, недоступным после группировки.
