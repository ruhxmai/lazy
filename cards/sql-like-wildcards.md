---
id: sql-like-wildcards
category: Backend
difficulty: junior
daily: true
---

# Как работают символы-маски `%` и `_` в SQL `LIKE`?

## Ответ

- `%` — любое количество любых символов (в т.ч. ноль)
- `_` — ровно один любой символ

```sql
SELECT * FROM users WHERE email LIKE '%@gmail.com';  -- заканчивается на @gmail.com
SELECT * FROM users WHERE name LIKE 'A%';             -- начинается на A
SELECT * FROM users WHERE name LIKE '_ohn';           -- John, Sohn, но не Johnny
SELECT * FROM users WHERE name LIKE '%oh%';           -- содержит "oh" где угодно
```

Чтобы искать сам символ `%` или `_` буквально, его экранируют:

```sql
SELECT * FROM discounts WHERE code LIKE '50\%' ESCAPE '\'; -- ищет буквально "50%"
```

**Важно про производительность:** индекс на колонке эффективно используется, только если `%` **не стоит в начале** шаблона. `LIKE 'A%'` может использовать индекс, а `LIKE '%A'` или `LIKE '%A%'`, как правило, нет — превращается в полное сканирование таблицы.
