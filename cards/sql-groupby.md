---
id: sql-groupby
category: Backend
daily: true
---

# Чем отличается WHERE от HAVING в SQL?

## Ответ

`WHERE` фильтрует строки **до** группировки, `HAVING` — **после**.

```sql
-- Отделы, где средняя зарплата активных сотрудников > 50000
SELECT department, AVG(salary) AS avg_salary
FROM employees
WHERE status = 'active'       -- фильтр строк до группировки
GROUP BY department
HAVING AVG(salary) > 50000;   -- фильтр групп после GROUP BY
```

**Правило:** в `WHERE` нельзя использовать агрегатные функции (`COUNT`, `AVG`, `SUM`, `MAX`, `MIN`) — только в `HAVING`.

```sql
WHERE  AVG(salary) > 50000   -- ❌ синтаксическая ошибка
HAVING AVG(salary) > 50000   -- ✅
```
