---
id: sql-indexes
category: Backend
daily: true
---

# Что такое индексы в SQL и зачем они нужны?

## Ответ

**Индекс** — структура данных (обычно B-Tree), ускоряющая поиск строк. Без индекса — full table scan O(n), с индексом — O(log n).

```sql
-- Создание индекса
CREATE INDEX idx_users_email ON users(email);

-- Составной индекс (порядок колонок важен!)
CREATE INDEX idx_orders ON orders(user_id, created_at);

-- Проверка плана запроса
EXPLAIN SELECT * FROM users WHERE email = 'test@example.com';
```

**Когда индексы не нужны:**
- Маленькие таблицы (full scan быстрее)
- Колонки с малой кардинальностью (`boolean`, `status`)
- Часто обновляемые колонки

Индексы ускоряют `SELECT`, но замедляют `INSERT`/`UPDATE`/`DELETE`.
