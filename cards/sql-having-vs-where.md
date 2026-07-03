---
id: sql-having-vs-where
category: Backend
difficulty: junior
daily: true
---

# В чём разница между WHERE и HAVING?

## Ответ

**WHERE** фильтрует строки **до** группировки (`GROUP BY`), работает с исходными колонками:

```sql
SELECT department, salary
FROM employees
WHERE salary > 50000;
-- Фильтрует отдельные строки сотрудников
```

**HAVING** фильтрует группы **после** агрегации, работает с результатами агрегатных функций (`SUM`, `COUNT`, `AVG`):

```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
-- Оставляет только отделы, где средняя зарплата > 50000
```

Можно использовать оба вместе — `WHERE` сузит данные до группировки, `HAVING` отфильтрует уже сгруппированный результат:

```sql
SELECT department, COUNT(*) AS cnt
FROM employees
WHERE hired_at > '2020-01-01'
GROUP BY department
HAVING COUNT(*) > 5;
```

**Правило:** `WHERE` нельзя использовать с агрегатными функциями — для этого существует `HAVING`.
