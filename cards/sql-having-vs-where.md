---
id: sql-having-vs-where
category: Backend
difficulty: junior
daily: true
---

# В чём разница между `WHERE` и `HAVING` в SQL?

## Ответ

`WHERE` фильтрует строки **до** группировки (`GROUP BY`), `HAVING` — фильтрует группы **после** агрегации.

```sql
SELECT department, COUNT(*) AS cnt
FROM employees
WHERE status = 'active'      -- фильтр строк до группировки
GROUP BY department
HAVING COUNT(*) > 5;         -- фильтр групп после агрегации
```

- В `WHERE` нельзя использовать агрегатные функции (`COUNT`, `SUM`, `AVG`...) — на этом этапе группы ещё не существуют.
- В `HAVING` агрегатные функции — это основной сценарий использования.
- Порядок выполнения запроса: `FROM` → `WHERE` → `GROUP BY` → `HAVING` → `SELECT` → `ORDER BY`.

```sql
-- Ошибка: агрегат в WHERE
SELECT department, COUNT(*) FROM employees WHERE COUNT(*) > 5 GROUP BY department;
```
