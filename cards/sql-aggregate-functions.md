---
id: sql-aggregate-functions
category: Backend
difficulty: junior
daily: true
---

# Какие есть агрегатные функции в SQL и как их использовать с GROUP BY?

## Ответ

Агрегатные функции сворачивают множество строк в одно значение:

| Функция | Что делает |
|---|---|
| `COUNT()` | Количество строк |
| `SUM()` | Сумма значений |
| `AVG()` | Среднее значение |
| `MIN()` / `MAX()` | Минимум / максимум |

```sql
-- Количество заказов и средний чек по каждому клиенту
SELECT customer_id,
       COUNT(*)   AS orders_count,
       AVG(total) AS avg_check
FROM orders
GROUP BY customer_id;
```

- Без `GROUP BY` агрегатная функция считается по всей таблице сразу: `SELECT COUNT(*) FROM orders;`
- `COUNT(*)` считает все строки, `COUNT(column)` — только строки, где `column` не `NULL`
- Каждая колонка в `SELECT`, которая не под агрегатной функцией, должна быть в `GROUP BY`
