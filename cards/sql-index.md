---
id: sql-index
category: Backend
daily: true
---

# Что такое индекс в SQL и зачем он нужен?

## Ответ

**Индекс** — структура данных (обычно B-дерево), которая ускоряет поиск строк. Без индекса — полный перебор таблицы (full scan), с индексом — поиск за O(log n).

```sql
-- Обычный индекс
CREATE INDEX idx_users_email ON users(email);

-- Составной индекс (порядок колонок важен!)
CREATE INDEX idx_orders_user_date ON orders(user_id, created_at);

-- Уникальный индекс
CREATE UNIQUE INDEX idx_unique_email ON users(email);

-- Проверить, используется ли индекс
EXPLAIN SELECT * FROM users WHERE email = 'test@example.com';
```

**Минусы индексов:**
- Замедляют `INSERT` / `UPDATE` / `DELETE`
- Занимают место на диске

Индексируй колонки, по которым часто фильтруешь: `WHERE`, `JOIN`, `ORDER BY`.
