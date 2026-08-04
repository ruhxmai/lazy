---
id: sql-union-vs-union-all
category: Backend
difficulty: junior
daily: true
---

# Чем UNION отличается от UNION ALL?

## Ответ

Оба объединяют результаты двух `SELECT`-запросов с одинаковым числом и типами столбцов, но:

- **UNION** — убирает дубликаты строк (делает неявный `DISTINCT`), поэтому медленнее
- **UNION ALL** — оставляет все строки как есть, включая дубликаты, работает быстрее

```sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
-- каждый город встретится только один раз

SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;
-- город может повторяться, если есть и там, и там
```

Правило: если известно, что дубликатов не будет (или они не важны), используй `UNION ALL` — он не тратит время на сравнение и удаление повторов.
