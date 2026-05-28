---
id: sql-indexes
category: Backend
difficulty: junior
daily: true
---

# Что такое индекс в SQL и зачем он нужен?

## Ответ

**Индекс** — структура данных (обычно B-tree), которая ускоряет поиск строк, не перебирая всю таблицу.

```sql
-- Простой индекс
CREATE INDEX idx_users_email ON users(email);

-- Составной индекс (порядок колонок важен!)
CREATE INDEX idx_orders_user_date ON orders(user_id, created_at);

-- Уникальный индекс
CREATE UNIQUE INDEX idx_users_email_unique ON users(email);
```

| | Без индекса | С индексом |
|---|---|---|
| SELECT по email | Full table scan O(n) | B-tree lookup O(log n) |
| INSERT / UPDATE | Быстро | Чуть медленнее |

**Когда ставить:** на колонки в `WHERE`, `JOIN ON`, `ORDER BY` при работе с большими таблицами (> 10k строк).

**Когда не надо:** маленькие таблицы, часто обновляемые колонки.
