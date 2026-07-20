---
id: sql-union-vs-union-all
category: Backend
difficulty: junior
daily: true
---

# Чем `UNION` отличается от `UNION ALL` в SQL?

## Ответ

Оба объединяют результаты двух `SELECT`-запросов **с одинаковым числом и типом колонок** в одну выборку.

- **`UNION`** удаляет дубликаты строк из итогового результата (неявно делает `DISTINCT`).
- **`UNION ALL`** оставляет все строки как есть, включая дубликаты.

```sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
-- уникальные города из обеих таблиц

SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;
-- все города, включая повторы
```

**Важно про производительность:** `UNION` тратит дополнительное время на поиск и удаление дубликатов (обычно через сортировку или хеширование), поэтому он **медленнее** `UNION ALL`. Если вы точно знаете, что дубликатов не будет (или они не важны), используйте `UNION ALL`.

```sql
-- Если id уникальны в разных таблицах — UNION ALL безопасен и быстрее
SELECT id, name FROM active_users
UNION ALL
SELECT id, name FROM archived_users;
```
