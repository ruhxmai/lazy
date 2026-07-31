---
id: sql-union
category: Backend
difficulty: junior
daily: true
---

# Чем UNION отличается от UNION ALL?

## Ответ

Оба объединяют результаты двух запросов с одинаковым числом столбцов.

**UNION** — убирает дубликаты (по сути делает `DISTINCT`), поэтому медленнее:

```sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
```

**UNION ALL** — оставляет все строки, включая дубликаты, работает быстрее:

```sql
SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;
```

Правило: если знаешь, что дубликатов нет или они не важны — используй `UNION ALL`, это дешевле для БД.
