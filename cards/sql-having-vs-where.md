---
id: sql-having-vs-where
category: Backend
daily: true
---

# В чём разница между `WHERE` и `HAVING`?

## Ответ

`WHERE` фильтрует **строки до** группировки, `HAVING` фильтрует **группы после** `GROUP BY` / агрегатных функций.

```sql
-- WHERE: работает со строками исходной таблицы,
-- нельзя использовать агрегатные функции (COUNT, SUM, ...)
SELECT department, COUNT(*) AS cnt
FROM employees
WHERE salary > 50000
GROUP BY department
HAVING COUNT(*) > 5;
-- HAVING: работает с результатом группировки,
-- фильтрует уже посчитанные агрегаты
```

Порядок выполнения запроса: `FROM` → `WHERE` → `GROUP BY` → `HAVING` → `SELECT` → `ORDER BY`.

Поэтому `WHERE COUNT(*) > 5` вызовет ошибку — на этом этапе агрегат ещё не посчитан, а `HAVING salary > 50000` работать не будет как ожидается, если это не агрегатное выражение.
