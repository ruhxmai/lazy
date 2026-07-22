---
id: sql-having-vs-where
category: Backend
difficulty: junior
daily: true
---

# В чём разница между WHERE и HAVING?

## Ответ

`WHERE` фильтрует **строки до группировки**, `HAVING` — фильтрует **группы после `GROUP BY`**. `WHERE` не умеет работать с агрегатными функциями (`COUNT`, `SUM`, `AVG`), а `HAVING` умеет.

```sql
SELECT department, COUNT(*) AS cnt
FROM employees
WHERE active = true         -- фильтр строк ДО группировки
GROUP BY department
HAVING COUNT(*) > 5;        -- фильтр групп ПОСЛЕ группировки
```

Если написать `WHERE COUNT(*) > 5`, будет ошибка — на момент выполнения `WHERE` агрегаты ещё не посчитаны.
