---
id: sql-where
category: Backend
daily: true
---
# Как фильтровать и сортировать данные в SQL?
## Ответ
Используй `WHERE`, `ORDER BY`, `LIMIT` и `HAVING`.

```sql
-- Фильтрация строк
SELECT * FROM users
WHERE age > 18 AND city = 'Moscow';

-- Сортировка (ASC по умолчанию, DESC — по убыванию)
SELECT * FROM products
ORDER BY price DESC
LIMIT 10;

-- HAVING — фильтр после GROUP BY (по агрегату)
SELECT department, COUNT(*) AS cnt
FROM employees
GROUP BY department
HAVING cnt > 5;
```

`WHERE` работает **до** агрегации, `HAVING` — **после**.
