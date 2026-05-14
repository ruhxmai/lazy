---
id: sql-indexes
category: Backend
difficulty: junior
daily: true
---

# Что такое индекс в SQL и зачем он нужен?

## Ответ

Индекс — структура данных (обычно B-дерево), ускоряющая поиск по таблице. Без индекса база сканирует все строки (full table scan).

```sql
-- Обычный индекс
CREATE INDEX idx_users_email ON users(email);

-- Составной индекс
CREATE INDEX idx_orders_user_date ON orders(user_id, created_at);

-- Уникальный индекс
CREATE UNIQUE INDEX idx_users_email_uniq ON users(email);
```

**Плюсы:** быстрый `SELECT` по индексированным колонкам
**Минусы:** замедляет `INSERT`/`UPDATE`/`DELETE`, занимает дисковое место

- Индексируй колонки в `WHERE`, `JOIN ON`, `ORDER BY`
- Не ставь индекс на колонки с малым числом уникальных значений (например, boolean)
