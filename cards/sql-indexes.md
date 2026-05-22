---
id: sql-indexes
category: Backend
daily: true
---
# Что такое индексы в SQL и зачем они нужны?

## Ответ

**Индекс** — структура данных (обычно B-tree), которая ускоряет поиск строк. Без индекса — `full table scan` O(n), с индексом — O(log n).

```sql
-- Обычный индекс
CREATE INDEX idx_users_email ON users(email);

-- Составной индекс (порядок колонок важен!)
CREATE INDEX idx_orders ON orders(user_id, created_at);

-- Проверить план запроса
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'a@b.com';
```

**Минусы:**
- Замедляют `INSERT` / `UPDATE` / `DELETE` (нужно обновить индекс)
- Занимают место на диске

**Правило:** добавляй индексы на колонки в `WHERE`, `JOIN ON`, `ORDER BY` для больших таблиц.
