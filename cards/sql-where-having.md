---
id: sql-where-having
category: Backend
daily: true
---
# В чём разница между WHERE и HAVING в SQL?

## Ответ

- `WHERE` — фильтрует строки **до** группировки (`GROUP BY`)
- `HAVING` — фильтрует группы **после** группировки

```sql
SELECT department, COUNT(*) AS total
FROM employees
WHERE salary > 50000          -- фильтр строк ДО GROUP BY
GROUP BY department
HAVING COUNT(*) > 3;          -- фильтр групп ПОСЛЕ GROUP BY
```

`HAVING` может использовать агрегатные функции (`COUNT`, `SUM`, `AVG`), `WHERE` — нет. Если условие не зависит от агрегации — всегда пиши в `WHERE`, это быстрее.
