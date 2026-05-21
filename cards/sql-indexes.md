---
id: sql-indexes
category: Backend
daily: true
---
# Что такое индекс в SQL и зачем он нужен?
## Ответ
Индекс — это структура данных (обычно B-tree), которая ускоряет поиск строк в таблице, избегая полного перебора (full table scan).

**Плюсы:** быстрый `SELECT` / `WHERE` / `JOIN`  
**Минусы:** медленнее `INSERT` / `UPDATE` / `DELETE`, занимает дополнительное место

```sql
-- Обычный индекс
CREATE INDEX idx_users_email ON users(email);

-- Уникальный индекс (гарантирует уникальность значений)
CREATE UNIQUE INDEX idx_unique_email ON users(email);

-- Составной индекс (порядок колонок важен!)
CREATE INDEX idx_name_age ON users(last_name, age);
```

Правило: индексируй колонки, по которым часто фильтруешь (`WHERE`) или джойнишь (`JOIN`).
