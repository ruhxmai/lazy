---
id: sql-indexes
category: Backend
daily: true
---
# Что такое индекс в SQL и зачем он нужен?
## Ответ
Индекс — отдельная структура данных (обычно B-tree), ускоряющая поиск строк. Без индекса БД делает **full table scan** — проходит по всем строкам.

```sql
-- Простой индекс
CREATE INDEX idx_users_email ON users(email);

-- Составной индекс
CREATE INDEX idx_orders_user_date ON orders(user_id, created_at);

-- Посмотреть план запроса
EXPLAIN SELECT * FROM users WHERE email = 'a@b.com';
```

**Плюсы:** быстрый `SELECT` по индексированному полю.  
**Минусы:** замедляет `INSERT` / `UPDATE` / `DELETE`, занимает место на диске.

Индексировать стоит колонки в `WHERE`, `JOIN ON`, `ORDER BY`.
