---
id: sql-indexes
category: Backend
daily: true
---
# Что такое индекс в SQL и зачем он нужен?
## Ответ
Индекс — структура данных (чаще всего B-дерево), которая ускоряет поиск строк в таблице. Без индекса база данных выполняет full scan — просматривает каждую строку.

**Плюсы:** быстрый `SELECT` по индексированному столбцу.  
**Минусы:** замедляет `INSERT` / `UPDATE` / `DELETE`, занимает место на диске.

```sql
-- Простой индекс по одному столбцу
CREATE INDEX idx_users_email ON users(email);

-- Составной индекс (порядок столбцов важен!)
CREATE INDEX idx_orders_user_date ON orders(user_id, created_at);

-- Уникальный индекс — гарантирует отсутствие дублей
CREATE UNIQUE INDEX idx_users_email_unique ON users(email);

-- Посмотреть план запроса
EXPLAIN SELECT * FROM users WHERE email = 'test@example.com';
```

Индексы автоматически создаются для `PRIMARY KEY` и `UNIQUE` ограничений.
