---
id: sql-subqueries
category: Backend
difficulty: junior
daily: true
---

# Что такое подзапрос (subquery) в SQL?

## Ответ

Подзапрос — это SELECT-запрос **внутри другого запроса**. Используется для фильтрации, вычислений или сравнений.

```sql
-- Найти пользователей с хотя бы одним заказом
SELECT name
FROM users
WHERE id IN (
  SELECT user_id
  FROM orders
);

-- Найти товары дороже средней цены
SELECT name, price
FROM products
WHERE price > (
  SELECT AVG(price)
  FROM products
);
```

**Типы подзапросов:**
- **Scalar** — возвращает одно значение (в `WHERE`, `SELECT`)
- **Table subquery** — возвращает таблицу (в `FROM` или `JOIN`)
- **Correlated** — ссылается на внешний запрос (выполняется построчно)

> Для лучшей производительности часто предпочитают `JOIN` вместо подзапросов — оптимизатор БД справляется с ними лучше.
