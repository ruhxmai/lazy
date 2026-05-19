---
id: sql-indexes
category: Backend
daily: true
---
# Что такое индекс в SQL и когда его добавлять?

## Ответ
Индекс — структура данных (B-tree), ускоряющая поиск строк по колонке. Без индекса база делает **full table scan** — перебирает все строки.

```sql
-- создать индекс
CREATE INDEX idx_users_email ON users(email);

-- составной индекс
CREATE INDEX idx_orders ON orders(user_id, created_at);

-- запрос автоматически использует индекс
SELECT * FROM users WHERE email = 'alice@mail.com';
```

**Компромисс:** индекс ускоряет `SELECT`, но замедляет `INSERT/UPDATE/DELETE`. Добавляй на колонки с частыми `WHERE`, `JOIN`, `ORDER BY`.
