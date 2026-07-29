---
id: sql-union
category: Backend
daily: true
---

# Чем отличается UNION от UNION ALL в SQL?

## Ответ

Оба оператора объединяют результаты двух `SELECT`-запросов **вертикально** (строки друг под другом), но:

- `UNION` — убирает дубликаты строк (делает неявный `DISTINCT`)
- `UNION ALL` — оставляет все строки, включая дубликаты

```sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
-- Каждый город встретится один раз, даже если есть и там, и там
```

```sql
SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;
-- Города могут повторяться
```

**Требования:** оба запроса должны возвращать одинаковое количество колонок с совместимыми типами данных. Имена колонок берутся из первого `SELECT`.

**Производительность:** `UNION` медленнее — ему нужно отсортировать/захешировать все строки, чтобы найти дубликаты. Если знаешь, что дубликатов не будет (или они не важны), используй `UNION ALL` — он просто склеивает результаты без лишней работы.

```sql
-- Плохо, если дубликаты не важны: лишняя работа по дедупликации
SELECT id FROM archived_orders
UNION
SELECT id FROM active_orders;

-- Хорошо: быстрее, если id гарантированно не пересекаются
SELECT id FROM archived_orders
UNION ALL
SELECT id FROM active_orders;
```
