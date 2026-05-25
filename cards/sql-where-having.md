---
id: sql-where-having
category: Backend
daily: true
---
# В чём разница между WHERE и HAVING в SQL?
## Ответ
`WHERE` фильтрует строки **до** группировки — нельзя использовать агрегатные функции (`COUNT`, `SUM`).  
`HAVING` фильтрует группы **после** `GROUP BY` — можно использовать агрегаты.

```sql
SELECT department, COUNT(*) AS cnt
FROM employees
WHERE salary > 50000        -- фильтр строк до группировки
GROUP BY department
HAVING COUNT(*) > 5;        -- фильтр групп после группировки
```

Правило: если нужна агрегатная функция в условии — используй `HAVING`, иначе — `WHERE`.
