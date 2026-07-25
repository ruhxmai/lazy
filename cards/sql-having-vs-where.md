---
id: sql-having-vs-where
category: Backend
daily: true
---

# Чем HAVING отличается от WHERE?

## Ответ

`WHERE` фильтрует **строки до группировки**, `HAVING` — фильтрует **группы после** `GROUP BY`. Из-за этого в `HAVING` можно использовать агрегатные функции (`COUNT`, `SUM`, `AVG`), а в `WHERE` — нельзя.

```sql
-- Найти клиентов с более чем 5 заказами на сумму от 1000
SELECT customer_id, COUNT(*) AS orders_count, SUM(amount) AS total
FROM orders
WHERE status = 'completed'        -- фильтр по строкам
GROUP BY customer_id
HAVING COUNT(*) > 5 AND SUM(amount) >= 1000  -- фильтр по группам
ORDER BY total DESC;
```

Порядок выполнения запроса важно понимать:

```
FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

Частая ошибка джуниора:

```sql
-- Не сработает: COUNT(*) не существует до группировки
SELECT customer_id, COUNT(*) FROM orders WHERE COUNT(*) > 5 GROUP BY customer_id;
```

Правило: если условие про **отдельную строку** — `WHERE`; если про **агрегат/группу** — `HAVING`.
