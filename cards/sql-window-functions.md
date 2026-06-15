---
id: sql-window-functions
category: Backend
daily: true
---
# Что такое оконные функции в SQL?
## Ответ
Оконные функции вычисляют результат по набору строк (окну) **без схлопывания** строк в одну, в отличие от `GROUP BY`. Используют `OVER()`.

```sql
SELECT
  name,
  salary,
  ROW_NUMBER() OVER (ORDER BY salary DESC) AS rank,
  AVG(salary) OVER (PARTITION BY department)  AS dept_avg
FROM employees;
```

Популярные функции: `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, `LAG()`, `LEAD()`, `SUM() OVER()`.
