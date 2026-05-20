---
id: sql-indexes
category: Backend
difficulty: junior
daily: true
---

# Что такое индекс в SQL и зачем он нужен?

## Ответ

Индекс — структура данных (обычно B-дерево), которая ускоряет поиск строк в таблице. Похоже на предметный указатель в книге.

```sql
-- Без индекса: полный перебор всей таблицы (Full Table Scan)
SELECT * FROM users WHERE email = 'alice@example.com';

-- Создать индекс по полю email
CREATE INDEX idx_users_email ON users(email);

-- Теперь поиск по email — быстрый (O(log n) вместо O(n))
SELECT * FROM users WHERE email = 'alice@example.com';

-- Уникальный индекс: гарантирует уникальность + ускоряет поиск
CREATE UNIQUE INDEX idx_users_email_uniq ON users(email);

-- Составной индекс (работает для запросов по first_name или first_name+last_name)
CREATE INDEX idx_name ON users(first_name, last_name);
```

- Ускоряет `SELECT`, замедляет `INSERT/UPDATE/DELETE` (нужно обновлять индекс)
- `PRIMARY KEY` и `UNIQUE` создают индекс автоматически
- Не индексируй всё подряд — каждый индекс занимает место на диске
