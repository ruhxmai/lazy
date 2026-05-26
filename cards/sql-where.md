---
id: sql-where
category: Backend
difficulty: junior
daily: true
---

# Как фильтровать строки в SQL с помощью WHERE?

## Ответ

`WHERE` фильтрует строки по условию. Можно комбинировать несколько операторов.

```sql
-- Базовое условие
SELECT * FROM users WHERE age > 18;

-- Несколько условий
SELECT * FROM users WHERE age > 18 AND city = 'Moscow';
SELECT * FROM users WHERE city = 'Moscow' OR city = 'SPb';

-- Поиск по шаблону (% — любое кол-во символов, _ — один символ)
SELECT * FROM users WHERE name LIKE 'Al%';

-- Список значений
SELECT * FROM users WHERE city IN ('Moscow', 'SPb', 'Kazan');

-- Диапазон
SELECT * FROM users WHERE age BETWEEN 18 AND 30;

-- Проверка на NULL
SELECT * FROM users WHERE email IS NULL;
SELECT * FROM users WHERE email IS NOT NULL;
```

- `LIKE` чувствителен к регистру в PostgreSQL, нечувствителен в MySQL
- `IN (...)` удобнее длинной цепочки `OR`
- Никогда не сравнивай NULL через `=` — только `IS NULL` / `IS NOT NULL`
