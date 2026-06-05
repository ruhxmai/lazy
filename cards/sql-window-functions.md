---
id: sql-window-functions
category: Backend
daily: true
---
# Что такое оконные функции (window functions) в SQL?
## Ответ
Оконные функции выполняют вычисления над «окном» строк, связанных с текущей строкой, **не сворачивая результат** — каждая строка остаётся в таблице.

```sql
SELECT
  name,
  salary,
  department,
  ROW_NUMBER() OVER (ORDER BY salary DESC)     AS rank,
  AVG(salary)  OVER (PARTITION BY department)  AS dept_avg,
  LAG(salary)  OVER (ORDER BY hire_date)       AS prev_salary
FROM employees;
```

Популярные функции:
- `ROW_NUMBER()` — порядковый номер без пропусков
- `RANK()` / `DENSE_RANK()` — ранг с пропусками / без
- `LAG(col)` / `LEAD(col)` — значение предыдущей / следующей строки
- `SUM()`, `AVG()` — агрегаты по окну без GROUP BY
