---
id: sql-select
category: Backend
daily: true
---

# Как работает базовый SELECT с WHERE и ORDER BY в SQL?

## Ответ

`SELECT` извлекает данные, `WHERE` фильтрует строки, `ORDER BY` сортирует результат.

```sql
-- Пользователи из Москвы, отсортированные по имени
SELECT id, name, email
FROM users
WHERE city = 'Moscow'
ORDER BY name ASC;

-- Виды условий WHERE
WHERE age > 18                    -- сравнение
WHERE status = 'active'           -- равенство
WHERE name LIKE 'А%'              -- начинается с «А»
WHERE city IN ('Moscow', 'SPb')   -- список значений
WHERE deleted_at IS NULL          -- проверка на NULL

-- Ограничение числа строк
SELECT * FROM products
ORDER BY price DESC
LIMIT 10;
```

Порядок слов: `SELECT → FROM → WHERE → ORDER BY → LIMIT`.
